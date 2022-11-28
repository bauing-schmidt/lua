
try {
	node('windows-slave-2') {
		try {
			checkout scm
bat '''
wget https://www.lua.org/ftp/lua-5.4.4.tar.gz
tar xfz lua-5.4.4.tar.gz
cd lua-5.4.4

mingw32-make.exe mingw

mkdir ../bin
cp src/*.exe ../bin

mkdir ../lib
cp src/liblua.a src/lua54.dll ../lib

mkdir ../include
cp src/lauxlib.h src/lua.h src/luaconf.h src/lualib.h src/lua.hpp ../include

zip -r ../lua.zip bin/ lib/ include/
'''
		} finally {
			archiveArtifacts artifacts: 'lua.zip'
			cleanWs()
		}
	}
} catch(e) {
	throw e
}
