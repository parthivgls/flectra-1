include Makefile.version
include Makefile.python
include Makefile.servicename

SERVER_DIRECTORY=../..
FILES_DIRECTORY=release

MAKENSIS_ARGUMENTS=/DVERSION=$(VERSION) /DSERVICENAME=${SERVICENAME}

LAUNCH_MAKENSIS=/cygdrive/c/tools/cygwin/makensis $(MAKENSIS_ARGUMENTS) setup.nsi

default: allinone

clean: server_clean
	rm -rf $(FILES_DIRECTORY)/*.exe
	rm -rf *.exe

server_clean:
	rm -rf $(SERVER_DIRECTORY)/dist 
	rm -rf $(SERVER_DIRECTORY)/build
	rm -rf $(SERVER_DIRECTORY)/win32/dist 
	rm -rf $(SERVER_DIRECTORY)/win32/build
	rm -rf $(SERVER_DIRECTORY)/*.exe
	rm -rf $(SERVER_DIRECTORY)/.cyg*

allinone: server_clean
	(cd $(SERVER_DIRECTORY)/setup/win32 && $(LAUNCH_MAKENSIS))
	(cd $(SERVER_DIRECTORY)/setup/win32 && mkdir -p $(FILES_DIRECTORY))
	(cd $(SERVER_DIRECTORY)/setup/win32 && cp flectra-*.exe $(FILES_DIRECTORY)/flectra-server-setup-$(VERSION).exe)
