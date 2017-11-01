# OpenGL / OpenGL Shading Language（GLSL）

## 用語

### Context

OpenGLのインスタンスに関連するすべてのstateを保持するもの。

* OpenGLを利用する際、プロセスはcontextを作成しその上で処理を実行する
  * 1つのプロセスが複数のcontextを保持することも可
* contextはそれぞれにOpenGL Objectsを保持しており、container object以外はcontext間での共有も可
* OpenGLコマンドはそのスレッドにおけるcurrent contextに対して操作を行う
  * 逆に言えば処理を実行したいcontextをcurrent contextにセットしてからコマンドを呼ばなければならない
* 複数のスレッドで同時に同じcontextをcurrent contextにすることはできない

### OpenGL Object

OpenGLの内部状態（state）は構造化されて管理されており、その構造をOpenGL Objectと呼ぶ。
OpenGLのAPIはObject単位で働きかけるよう設計されている。

* Objectは`glGen*`コマンドで作成する
* 各Objectはcontextにbindしないと何の動作もしない
  * 例外はProgram Pipeline ObjectsとSampler Objects
* Objectは`GLuint`型のIDで管理される
  * `0`以外の32bit unsigned integerが割り振られる
  * GL3.0では`glGen*`せずとも`3`を指定すればdefault stateを持ったObjectを指すようになっていたがGL3.1以降では廃止された
* Objectは`glDelete*`コマンドで削除する
  * current contextにbindされていればdeleteの際にunbindされる
  * current context以外にbindされていた場合はunbindされない
  * current contextを設定してから削除すべし
* Objectは`glBind*`コマンドでcurrent contextにbindする
* いくつかのObjectは特殊な方法でcontextにbindできる

## 書き方

### Vertex Buffer Object : VBO

プログラムからシェーダー（GLSL）側に頂点情報を渡すときに利用するオブジェクト。

<details><summary>Sample code</summary>

```cpp
// sample to draw static triangle polygon data with position info

GLuint program = glCreateProgram;

// ~~ compile shaders / link program ~~

std::vector<GLfloat> poss = {{0,0,0}, ....};

GLuint vbo;
glGenBuffers(1, &vbo); // create buffer
glBindBuffers(GL_ARRAY_BUFFER, vbo); // bind buffer as array buffer
// create buffer data field and initialize with verts
glBufferData(GL_ARRAY_BUFFER, sizeof(GLfloat) * poss.size(), &poss[0], GL_STATIC_DRAW);

// get "position" attribute id
// (assume that a vertex shader reserves "position")
// (it is an array of generic vertex attribute data)
GLint posIndex = glGetAttribLocation(program, "position");
// define an "position" attribute
glVertexAttribPointer(posIndex, 3, GL_FLOAT, GL_FALSE, 0, NULL);
// enable "position" attribute
glEnableVertexAttribArray(posIndex);

// in draw function
{
    glDrawArrays(GL_TRIANGLES, 0, 3);
}
```

</details>

### Vertex Array Object : VAO

プログラムからシェーダー（GLSL）側に頂点情報を渡すとき、「頂点座標と色」といった複数の属性情報を渡すために利用するオブジェクト。

<details><summary>Sample code</summary>

```cpp
// sample to draw static triangle polygon data with position and color info

GLuint program = glCreateProgram;

// ~~ compile shaders / link program ~~

std::vector<GLfloat> poss = {{0,0,0}, ....};
std::vector<GLfloat> colors = {{1,0,0}, ....};

GLuint vao;
glGenVertexArrays(1, &vao); // create vertex array
glBindVertexArray(vao); // bind vertex array

GLuint vbo[2];
glGenBuffers(2, &vbo); // create buffer

// == setup for "position" ==
// bind buffer as array buffer and current target buffer is vbo[0]
glBindBuffers(GL_ARRAY_BUFFER, vbo[0]);
// create buffer data field and initialize with verts
glBufferData(GL_ARRAY_BUFFER, sizeof(GLfloat) * poss.size(), &poss[0], GL_STATIC_DRAW);
// same operation as vbo example
GLint posIndex = glGetAttribLocation(program, "position");
glVertexAttribPointer(posIndex, 3, GL_FLOAT, GL_FALSE, 0, NULL);
glEnableVertexAttribArray(posIndex);

// == setup for "color" ==
glBindBuffers(GL_ARRAY_BUFFER, vbo[1]);
glBufferData(GL_ARRAY_BUFFER, sizeof(GLfloat) * colors.size(), &colors[0], GL_STATIC_DRAW);
GLint colorIndex = glGetAttribLocation(program, "color");
glVertexAttribPointer(colorIndex, 3, GL_FLOAT, GL_FALSE, 0, NULL);
glEnableVertexAttribArray(colorIndex);

// in draw function
{
    glDrawArrays(GL_TRIANGLES, 0, 3);
}
```

</details>

### Indexed VBO

頂点情報のインデックスを使って描画すべきポリゴンを指定する方法。
頂点情報を重複して渡す必要がなくなるのでメモリの節約になる。

<details><summary>Sample code</summary>

```cpp
// sample to draw static triangle polygon data with indexed position data and triangle info

// ~~ same as VBO sample code ~~

std::vector<GLuint> indexes = {{0,1,2}, ....};

GLuint ebo;
glGenBuffers(1, &ebo);
glBindBuffer(GL_ELEMENT_ARRAY_BUFFER, ebo);
glBufferData(GL_ELEMENT_ARRAY_BUFFER, indexes.size() * sizeof(GLuint), &indexes[0], GL_STATIC_DRAW);

// in draw function
{
    glDrawElements(GL_TRIANGLES, poss.size(), GL_UNSIGNED_INT, 0);
}
```

</details>
