# $FreeBSD$

LOADER_UFS_SUPPORT?=	yes
LOADER_CD9660_SUPPORT?=	no
LOADER_EXT2FS_SUPPORT?=	no
LOADER_NET_SUPPORT?=	yes
LOADER_NFS_SUPPORT?=	yes
LOADER_TFTP_SUPPORT?=	no
LOADER_GZIP_SUPPORT?=	no
LOADER_BZIP2_SUPPORT?=	no

.include <bsd.init.mk>

PROG=		ubldr
NEWVERSWHAT=	"U-Boot loader" ${MACHINE_ARCH}
INSTALLFLAGS=	-b
MAN=

# Architecture-specific loader code
SRCS=		start.S conf.c vers.c
SRCS+=		ucmpdi2.c

# Always add MI sources
HELP_FILES=	# Disable
.include	"${BOOTSRC}/loader.mk"
.PATH:		${SYSDIR}/libkern

LDFLAGS=	-nostdlib -static -T ${.CURDIR}/ldscript.powerpc

.include	"${BOOTSRC}/uboot.mk"

DPADD=		${LIBFICL} ${LIBUBOOT} ${LIBFDT} ${LIBUBOOT_FDT} ${LIBSA}
LDADD=		${LIBFICL} ${LIBUBOOT} ${LIBFDT} ${LIBUBOOT_FDT} ${LIBSA}

.include <bsd.prog.mk>
