**環境配置**

> OS:linux ubuntu 18.04

**安裝步驟**
1. 從[Golang官網](https://golang.org/dl/)下載go1.11.linux-amd64.tar.gz
2. 至下載資料夾解壓縮go1.11.linux-amd64.tar.gz到/usr/local
<pre><font color="#8AE234"><b>$</b></font><b> </b>sudo tar -C /usr/local -xzf go1.9.linux-amd64.tar.gz
</pre>
3. 編輯.bashrc，調整環境參數。
<pre><font color="#8AE234"><b>$</b></font><b> </b>vi ~/.bashrc 
</pre>
請加上以下四列：
```
export GOPATH=$HOME/go
export GOROOT=/usr/local/go
export PATH=$PATH:$GOPATH/bin
export PATH=$PATH:$GOROOT/bin
```
4. 有使用zsh的話，也要編輯.zshrc
<pre><font color="#8AE234"><b>$</b></font><b> </b>vi ~/.zshrc 
</pre>
請加上以下四列：
```
export GOPATH=$HOME/go
export GOROOT=/usr/local/go
export PATH=$PATH:$GOPATH/bin
export PATH=$PATH:$GOROOT/bin
```
說明：
> 第3點與第4點中的GOPATH是指日後開發的Golang專案程式碼放置的資料夾位置（工作資料夾），GOROOT是指Golang安裝的資料夾位置。

5. 確認Golang有無安裝成功。
<pre><font color="#8AE234"><b>$</b></font><b> </b>go version
go version go1.11 linux/amd64
</pre>
6. 確認Golang環境設定。
<pre><font color="#8AE234"><b>$</b></font><b> </b>go env
GOARCH=&quot;amd64&quot;
GOBIN=&quot;&quot;
GOCACHE=&quot;/home/michael/.cache/go-build&quot;
GOEXE=&quot;&quot;
GOFLAGS=&quot;&quot;
GOHOSTARCH=&quot;amd64&quot;
GOHOSTOS=&quot;linux&quot;
GOOS=&quot;linux&quot;
GOPATH=&quot;/home/michael/go&quot;
GOPROXY=&quot;&quot;
GORACE=&quot;&quot;
GOROOT=&quot;/usr/local/go&quot;
GOTMPDIR=&quot;&quot;
GOTOOLDIR=&quot;/usr/local/go/pkg/tool/linux_amd64&quot;
GCCGO=&quot;gccgo&quot;
CC=&quot;gcc&quot;
CXX=&quot;g++&quot;
CGO_ENABLED=&quot;1&quot;
GOMOD=&quot;&quot;
CGO_CFLAGS=&quot;-g -O2&quot;
CGO_CPPFLAGS=&quot;&quot;
CGO_CXXFLAGS=&quot;-g -O2&quot;
CGO_FFLAGS=&quot;-g -O2&quot;
CGO_LDFLAGS=&quot;-g -O2&quot;
PKG_CONFIG=&quot;pkg-config&quot;
GOGCCFLAGS=&quot;-fPIC -m64 -pthread -fmessage-length=0 -fdebug-prefix-map=/tmp/go-build899480533=/tmp/go-build -gno-record-gcc-switches&quot;
</pre>
7. Golang專案資料夾結構說明：
> 請先確認Golang 工作資料夾（GOPATH）底下有無 bin、pkg、src 資料夾，若無請自行創建，資料夾的說明如下：

bin:放置go install生成的檔案。
pkg:放置go build後的檔案。
src:開發專案的資料夾位置。

實際體驗一下：
<pre><font color="#8AE234"><b>$</b></font><b> </b>cd ~ &amp;&amp; go install github.com/m24927605/go_helloworld
</pre>
<pre><font color="#8AE234"><b>$</b></font><b> </b>cd ~/go/bin &amp;&amp; ls
<font color="#8AE234"><b>go_helloworld</b></font>
</pre>
而且可以直接在terminal下go_helloworld
<pre>
<font color="#8AE234"><b>$</b></font><b> </b>go_helloworld
Hello World
</pre>


8. go get介紹
```
go get -v src/github.com/[user name]/[project name] 
```
說明：使用go get其實就是使用了git去拉取資源，相當於：
```
git clone https://github.com/[user name]/[
project name]
```
如果遠端資源有更新可以加上-u進行更新的拉取。
```
go get -v -u src/github.com/[user name]/[project name]
```