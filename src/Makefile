include ../Makefile.common

.DEFAULT_GOAL := all

EC_TARGETS ?= bn_sike751.ec
ASM_TARGETS ?= bn_sike751.s

all: test751 test610 test503 test434

test751: test_bn_sike751.c bn_sike751.s
	gcc -o $@ $^

test610: test_bn_sike610.c bn_sike610.s
	gcc -o $@ $^

test503: test_bn_sike503.c bn_sike503.s
	gcc -o $@ $^

test434: test_bn_sike434.c bn_sike434.s
	gcc -o $@ $^

sfiles: asm-clean $(ASM_TARGETS)

ecfiles: $(EC_TARGETS)

bn_generic.s : GFLAGS += -D BN_GENERIC_EXPORT
bn_generic.ec : GFLAGS += -D BN_GENERIC_TOEC

bn_sike751.s : GFLAGS += -D BN_SIKE751_EXPORT
bn_sike751.ec : GFLAGS += -D BN_SIKE751_TOEC

bn_sike610.s : GFLAGS += -D BN_SIKE610_EXPORT
bn_sike610.ec : GFLAGS += -D BN_SIKE610_TOEC

bn_sike503.s : GFLAGS += -D BN_SIKE503_EXPORT
bn_sike503.ec : GFLAGS += -D BN_SIKE503_TOEC

bn_sike434.s : GFLAGS += -D BN_SIKE434_EXPORT
bn_sike434.ec : GFLAGS += -D BN_SIKE434_TOEC

asm-clean:
	@rm -f fail *.japp $(ASM_TARGETS)
ec-clean:
	@rm -f fail Array*.ec WArray*.ec $(EC_TARGETS)

clean: asm-clean ec-clean
