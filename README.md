# PostSystem
ToDo:
●同一アプリ複数起動対策</br>
●アプリ異常終了時にサーバー一覧から自サーバーを削除する仕組み</br>

使い方</br>
//Newした時点でサーバーが立ち上がる</br>
LocalPost l_post = new LocalPost(Assembly.GetExecutingAssembly().GetName().Name, continueAction);</br>

・引数１はDLLを立ち上げたアプリの名前を渡す。アプリ名のサーバーが立ち上がってサーバーリストに登録される。</br>
・引数２はサーバーがクライアントからアクセスを受けて、レスポンスを返した後に実行される関数（Action<string>）を渡す。</br>
ここで送られてきた情報を処理する形。</br>
ServerCloseの通信がきたら終了する。</br>

  
//Sendした時点でクライアントが立ち上がる</br>
l_post.SendData(l_post.CreateSendData(送信データの形式（）, "送信データ", "送信先"))</br>
 ・引数1:送信データは専用関数で作成</br>
　※送信先は指定しない場合リストの全サーバーに送信。サーバーを閉じたい場合などに使用</br>
　※送信先サーバーがない場合送信待機状態になり、サーバーが立ち上がり次第送信される</br>
　※送信後サーバーからのResponseを受け取ったら勝手に終了する</br>
