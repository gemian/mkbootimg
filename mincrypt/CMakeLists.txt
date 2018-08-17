add_library(
		libmincrypt STATIC
		dsa_sig.c
		p256.c
		p256_ec.c
		p256_ecdsa.c
		rsa.c
		sha256.c
		sha.c
)
