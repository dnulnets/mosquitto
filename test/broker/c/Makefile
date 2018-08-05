.PHONY: all test clean reallyclean 08

include ../../../config.mk

CFLAGS=-I../../../lib -I../../../src -Wall -Werror

all : auth_plugin.so auth_plugin_pwd.so auth_plugin_acl.so auth_plugin_v2.so 08

08 : 08-tls-psk-pub.test 08-tls-psk-bridge.test

auth_plugin.so : auth_plugin.c
	$(CC) ${CFLAGS} -fPIC -shared $^ -o $@ 

auth_plugin_pwd.so : auth_plugin_pwd.c
	$(CC) ${CFLAGS} -fPIC -shared $^ -o $@ 

auth_plugin_acl.so : auth_plugin_acl.c
	$(CC) ${CFLAGS} -fPIC -shared $^ -o $@ 

auth_plugin_v2.so : auth_plugin_v2.c
	$(CC) ${CFLAGS} -fPIC -shared $^ -o $@ 

08-tls-psk-pub.test : 08-tls-psk-pub.c
ifneq ($(WITH_STATIC_LIBRARIES),yes)
	$(CC) ${CFLAGS} $^ -o $@ ../../../lib/libmosquitto.so.1
else
	$(CC) ${CFLAGS} $(FIPS_CFLAGS) $^ -o $@ $(FIPS_LDFLAGS) ../../../lib/libmosquitto.a -lssl -lcrypto -pthread -ldl
endif

08-tls-psk-bridge.test : 08-tls-psk-bridge.c
ifneq ($(WITH_STATIC_LIBRARIES),yes)
	$(CC) ${CFLAGS} $^ -o $@ ../../../lib/libmosquitto.so.1
else
	$(CC) ${CFLAGS} $(FIPS_CFLAGS) $^ -o $@ $(FIPS_LDFLAGS) ../../../lib/libmosquitto.a -lssl -lcrypto -pthread -ldl
endif

reallyclean : clean
	-rm -f *.orig

clean :
	rm -f *.so *.test
