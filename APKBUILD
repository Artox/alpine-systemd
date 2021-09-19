# Contributor: Josua Mayer <josua.mayer@jm0.eu>
# Maintainer:
pkgname=libsystemd
pkgver=249
pkgrel=0
pkgdesc="unix system services and facilities manager"
url="https://systemd.io/"
arch="all"
license="GPL-2.0"
depends=""
makedepends="bash coreutils gperf libcap-dev meson musl-dev musl-libintl python3 py3-jinja2 util-linux-dev"
checkdepends=""
install=""
subpackages="$pkgname-dev"
source="systemd-$pkgver.tar.gz::https://github.com/systemd/systemd/archive/refs/tags/v$pkgver.tar.gz
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0001-binfmt-Don-t-install-dependency-links-at-install-tim.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0001-systemd.pc.in-use-ROOTPREFIX-without-suffixed-slash.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0001-test-parse-argument-Include-signal.h.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0002-don-t-use-glibc-specific-qsort_r.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0003-implment-systemd-sysv-install-for-OE.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0003-missing_type.h-add-__compare_fn_t-and-comparison_fn_.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0004-add-fallback-parse_printf_format-implementation.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0005-src-basic-missing.h-check-for-missing-strndupa.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0006-Include-netinet-if_ether.h.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0007-don-t-fail-if-GLOB_BRACE-and-GLOB_ALTDIRFUNC-is-not-.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0008-add-missing-FTW_-macros-for-musl.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0009-fix-missing-of-__register_atfork-for-non-glibc-build.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0010-Use-uintmax_t-for-handling-rlim_t.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0011-test-sizeof.c-Disable-tests-for-missing-typedefs-in-.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0012-don-t-pass-AT_SYMLINK_NOFOLLOW-flag-to-faccessat.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0013-Define-glibc-compatible-basename-for-non-glibc-syste.patch	
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0014-Do-not-disable-buffering-when-writing-to-oom_score_a.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0015-distinguish-XSI-compliant-strerror_r-from-GNU-specif.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0016-Hide-__start_BUS_ERROR_MAP-and-__stop_BUS_ERROR_MAP.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0017-missing_type.h-add-__compar_d_fn_t-definition.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0018-avoid-redefinition-of-prctl_mm_map-structure.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0019-Handle-missing-LOCK_EX.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0020-Fix-incompatible-pointer-type-struct-sockaddr_un.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0021-test-json.c-define-M_PIl.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0022-do-not-disable-buffer-in-writing-files.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0025-Handle-__cpu_mask-usage.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0026-Handle-missing-gshadow.patch
	https://git.openembedded.org/openembedded-core/plain/meta/recipes-core/systemd/systemd/0028-missing_syscall.h-Define-MIPS-ABI-defines-for-musl.patch
	1000-inc-netdev.patch
"
patch_args="-d systemd-$pkgver -p1"
builddir="$srcdir"
options="!check"

build() {
	abuild-meson \
		-Dsplit-usr=false \
		-Dsplit-bin=false \
		-Dstatic-libsystemd=false \
		-Dc_args="-D__UAPI_DEF_ETHHDR=0" \
		-Dadm-group=false \
		-Danalyze=false \
		-Dbacklight=false \
		-Dbinfmt=false \
		-Dblkid=false \
		-Dbump-proc-sys-fs-file-max=false \
		-Dbump-proc-sys-fs-nr-open=false \
		-Dcompat-mutable-uid-boundaries=false \
		-Dcoredump=false \
		-Dcreate-log-dirs=false \
		-Ddefault-kill-user-processes=false \
		-Defi=false \
		-Denvironment-d=false \
		-Dfexecve=false \
		-Dfdisk=false \
		-Dfirstboot=false \
		-Dfuzz-tests=false \
		-Dgshadow=false \
		-Dhibernate=false \
		-Dhostnamed=false \
		-Dhwdb=false \
		-Didn=false \
		-Dima=false \
		-Dinitrd=false \
		-Dinstall-tests=false \
		-Dkernel-install=false \
		-Dldconfig=false \
		-Dlink-networkd-shared=false \
		-Dlink-systemctl-shared=false \
		-Dlink-timesyncd-shared=false \
		-Dlink-udev-shared=false \
		-Dllvm-fuzz=false \
		-Dlocaled=false \
		-Dlog-trace=false \
		-Dlogind=false \
		-Dmachined=false \
		-Dmemory-accounting-default=false \
		-Dnetworkd=false \
		-Dnscd=false \
		-Dnss-myhostname=false \
		-Dnss-systemd=false \
		-Doomd=false \
		-Doss-fuzz=false \
		-Dpolkit=false \
		-Dportabled=false \
		-Dpstore=false \
		-Dquotacheck=false \
		-Drandomseed=false \
		-Dresolve=false \
		-Drfkill=false \
		-Dslow-tests=false \
		-Dsmack=false \
		-Dstandalone-binaries=false \
		-Dsysext=false \
		-Dsysusers=false \
		-Dtimedated=false \
		-Dtimesyncd=false \
		-Dtmpfiles=false \
		-Dtpm=false \
		-Dtranslations=false \
		-Duserdb=false \
		-Dutmp=false \
		-Dvalgrind=false \
		-Dvconsole=false \
		-Dwheel-group=false \
		-Dxdg-autostart=false \
		systemd-$pkgver build 

	meson compile ${JOBS:+-j${JOBS}} -C build
}

package() {
	DESTDIR="$srcdir/dist" meson install --no-rebuild -C build

	install -v -m755 -d "$pkgdir/usr/lib"
	install -v -m644 "$srcdir/dist/"usr/lib/libsystemd.so* "$pkgdir/usr/lib/"

	install -v -m755 -d "$pkgdir/usr/include/systemd"
	install -v -m644 "$srcdir/dist/"usr/include/systemd/*.h "$pkgdir/usr/include/systemd/"

	install -v -m755 -d "$pkgdir/usr/lib/pkgconfig"
	install -v -m644 "$srcdir/dist/"usr/lib/pkgconfig/libsystemd.pc "$pkgdir/usr/lib/pkgconfig/"
}

sha512sums="
0810d09cc32e4aaa4425ee5b7ddf129262b061ce159cbd43571fabda48285243d8f80b566379ece9215d531b9407ee45e1e72c71935644fea31c7bca1bbf540c  systemd-249.tar.gz
4500d653283019eee7a996753f56d5056d809d1f1635f6d84c6f8b4448ba2ee7482b8d211f8ac82c369ea6ddb10e1c0eede1cd9ff0f3bdbb5533b15f145d79d6  0001-binfmt-Don-t-install-dependency-links-at-install-tim.patch
3b5fa924ea91eb5dd6cbb221d21b3e34202ef598fdd35a4c4ad2f16c57ccdadde89dc876e88b8d2f8d3fcc24f0ffebc71a07f57a40b6551a7d11d9e0ba39c89c  0001-systemd.pc.in-use-ROOTPREFIX-without-suffixed-slash.patch
bebc443f005ef6986f2f9be1f331674215906bae70e7c6002a7f25d1cc7ae53c391246798bd79a6b1be997aa35aad5606bb14c9143787d324134d023fccf7e5c  0001-test-parse-argument-Include-signal.h.patch
9c580a86b0f17f6f0204804bef4726cc63b11fa85e427536963f780809d00c003d566298d07bb007e54e2e5216be709f9d1d9a372e467bcc09403e0e3c596774  0002-don-t-use-glibc-specific-qsort_r.patch
7afb2f868e032f65238ae3a2db34acb7c4213f511db2cf99ef0a3e6fcdbdf6d96e94dde4a7de940bdcabec1db6125dc7187f3f95f081f0812ef9dd67eb036d4e  0003-implment-systemd-sysv-install-for-OE.patch
4e9b04c49117ccdb3ac2efc446510387c85d7e697103acc1cac29f80bd7f3530f8b2be3e574a967ee058022e64aef14f469f49f0b4184b7a0befd546b91f9a30  0003-missing_type.h-add-__compare_fn_t-and-comparison_fn_.patch
379e19eafe709a5f53a37c0b9b5342189554aaf21076fe34ed5ad2b259d76698501f5a64a74530417061c383d0f9a8043d2e76305b9d752e1d587991062133b5  0004-add-fallback-parse_printf_format-implementation.patch
64dc082fc87284fc396cdd580b1b48f4acbf720eee3fbbc41ca0652cf7c443312649f4df2e0f6831327fbd2a34baa84d7bd0a2c8cdd7511a3fcfb5608280d349  0005-src-basic-missing.h-check-for-missing-strndupa.patch
596fe6889b7041ebb301b1ec697566c94a0693f6199e11330abd55e0cfb263bd3dc1bb03f7c9269d5202cfc2be2a4a188e256a04643f1388d8661ac617f713ab  0006-Include-netinet-if_ether.h.patch
08697732c5324964bb154f6aa82685c01a2e25ef4b6759c9bb0a2ee374d22250c1bde091a71f930b7ae51377d612e9106285664f3c07a62177e4c07bf3d2b15d  0007-don-t-fail-if-GLOB_BRACE-and-GLOB_ALTDIRFUNC-is-not-.patch
af0be6cd51dc3c196dd70525e18c8635c9b7cdd24a0c79f4df331b62988c1d7ab5a1cabfc2db56b2ebe8df72937ecb683adbd3a4fd45072a430b104526958064  0008-add-missing-FTW_-macros-for-musl.patch
f5c4e30d4a5630548d0c6eac6bf247c45b3f6ea5fd520ff3a16b07a4d433cb18cb8a8a7f919281dd8b56e151072218fb2ae987b79e0549d14116a60258a4e8c6  0009-fix-missing-of-__register_atfork-for-non-glibc-build.patch
d96522b42609e4f95375e3e590ccab7f310088c388e98bad561246f4904ec65b351b5f148b3944de93c4ef85d518ec2dd6972d633cd785cf205aee42bb9bb865  0010-Use-uintmax_t-for-handling-rlim_t.patch
fa76fcb1897757ddda11a09c422dd9ba413f36e639f8abf72be49976d89c699bc30264a2b116d06e837d74fb1d0a60496dc29b118f22160a594a9546c716381a  0011-test-sizeof.c-Disable-tests-for-missing-typedefs-in-.patch
f4e46320a622f17579eea78e7d27838aa4c11c2e066a3f9be2303b4a7bd399dc3e5ee1938eb1f204be2e4d6ff3972d9c37eb96fdd79ee8ebdb5f44de1d1b27ad  0012-don-t-pass-AT_SYMLINK_NOFOLLOW-flag-to-faccessat.patch
f259d5beb433c73597f9c18d86e9153ed2d7413ef017718ae1891381fde05aa4ea23f0cd7250a5c304a1fb504741f2044668b065e4781498f14e0c01948cba8e  0013-Define-glibc-compatible-basename-for-non-glibc-syste.patch
e6ba5c3672b325ef5ef4c2100247826a274a8c32936c9b87d4ad28ad31227acad404b43777011f7805364fc9f5b1a1d25ec69976137d28750dedf3856ddb1837  0014-Do-not-disable-buffering-when-writing-to-oom_score_a.patch
8e9720c348c3078188397cf5adcdc0180934c62adea8b9245de58c046dd56e449901d1aa270c2e68a8dac6d17744e7f68c005f359a4f6cb4c77ca338b45aa753  0015-distinguish-XSI-compliant-strerror_r-from-GNU-specif.patch
6e2a2b1eaab34692f654bcaf27e85cc7846bba81acac87ee4c4ba6e3f646f85a2335348f3831adc97ffc0635e6ba0f4cd64bf83b15ad0015ad3425a10ef18a2d  0016-Hide-__start_BUS_ERROR_MAP-and-__stop_BUS_ERROR_MAP.patch
a3cae0b44cc0656d71edc1fc47fde7cd7b767c35ec67e5c1bedbe0a0d2afd5c8f250e044ed82feefbfbfe5372164263a8ec72a193742ae2675d37a7d18f21714  0017-missing_type.h-add-__compar_d_fn_t-definition.patch
9e21e75c83c9b1b1cd47a25bc8552de8a9cf49afc99313d28bd793d04548f1acb92962ff0909dedd40c168ad2e747d6efef907ddf45a9ee913d1baedaaa23eb2  0018-avoid-redefinition-of-prctl_mm_map-structure.patch
c695f53f911d257a2178817032adcb26f3029e809b7b32bde503d15db0c45598dd0351107386ecc4caba7ea3e7a03d76f9a8e35600958d0e96b2e880c6024591  0019-Handle-missing-LOCK_EX.patch
c3b42e626d67922ca0669943fdd27aec605436326bb977cc7307460a776f28796b149fe70bb1bc3c6940b8fc86fa14fd28dbd85c4ccb87eb218883e034a3ea54  0020-Fix-incompatible-pointer-type-struct-sockaddr_un.patch
63ec89c0b25c3f737650d6e492da7b04365a0dcc24d0dd3f7974406b59d98898092fa050116294e2f8c38d2e01ef092d843e9158fe3e18b6239ae80b015f3ab8  0021-test-json.c-define-M_PIl.patch
e2d1b37f60b17fef18a88a432d6bcecc5a03c879aa46e06627c6c0497d77a079811451675c82acaac0ea8053a148d70edeb8e0000b67a6789e22f62891479e79  0022-do-not-disable-buffer-in-writing-files.patch
982cb8ec4f361778cbba36d17d1e18e596b0d0dca1bd5691a0ae914459178950810e71385e2e23fa672028b5a5ae057e9eaf81e7003a27c495371e7cf8738e6f  0025-Handle-__cpu_mask-usage.patch
b03adae2050931eda040ff541d17d54032206d989f7377b516c041d6e92f3415ac197c4c1c2451ecb5809035437798196232257a38286bb02568f327b3d19246  0026-Handle-missing-gshadow.patch
ccfe8c046361c3e9f32c35fdbcc96ddbecc26594a03e61d4a5a89da843eeaa5c95021cbfe51a93e0c442be8c7d921217f9d339a673f3eee00a9395520aed7a11  0028-missing_syscall.h-Define-MIPS-ABI-defines-for-musl.patch
cf107b87a0de5d1af5832bb51825d516d59e6698a5be46b451b09bfc7589964694b10364f3e8e7664219d32ec9b9a71d5ee08765a4a578059384556fb4e0d2af  1000-inc-netdev.patch
"
