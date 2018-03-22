v1.9.3
apr-1.5.2

curl -O http://mirrors.cnnic.cn/apache/subversion/subversion-1.9.3.tar.gz

apr-util-1.5.4
tar zxvf subversion-1.9.3.tar.gz
cd subversion-1.9.3

curl -O http://www.sqlite.org/sqlite-amalgamation-3071501.zip
unzip sqlite-amalgamation-3071501.zip
mv sqlite-amalgamation-3071501 sqlite-amalgamation

 ./configure --prefix=/usr/local/subversion --with-apr=/usr/local/apr-1.5.2 --with-apr-util=/usr/local/apr-util-1.5.4
make
make install

mkdir /usr/local/svndata/repos
cd /usr/local/svndata/repos
svnadmin create .