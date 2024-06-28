API_VERSION?=2
CFLAGS?=-O3 -shared -rdynamic -std=c99

all: ../out/libs ../out/libs/fmodstudio_fix.so ../out/libs/EOSSDK-Win64-Shipping.so ../out/libs/libsteam_api.so

clean:
	@rm -f ../out/libs/*

../out/libs:
	mkdir -p ../out/libs

../out/libs/fmodstudio_fix.so: ../out/libs fmodstudio_fix.c
       $(CC) -Wno-return-type $(CFLAGS) fmodstudio_fix.c -o ../out/libs/fmodstudio_fix.so

../out/libs/EOSSDK-Win64-Shipping.so: ../out/libs EOSSDK-Shipping-Stubs.c
	$(CC) -Wno-return-type $(CFLAGS) EOSSDK-Shipping-Stubs.c -o ../out/libs/EOSSDK-Win64-Shipping.so -D API_VERSION=$(API_VERSION)

../out/libs/libsteam_api.so: ../out/libs SteamStubs.c
       $(CC) -Wno-return-type $(CFLAGS) SteamStubs.c -o ../out/libs/libsteam_api.so
       @cp ../out/libs/libsteam_api.so ../out/libs/libsteam_api64.so
       @cp ../out/libs/libsteam_api.so ../out/libs/CSteamworks