include Makefile.include

AM_CPPFLAGS += -I$(builddir)

noinst_LIBRARIES = \
  libbitcoin_common.a
if USE_TOR
noinst_LIBRARIES += libbitcoin_tor.a
endif

bin_PROGRAMS =

if BUILD_BITCOIND
  bin_PROGRAMS += bitcoinplusd
endif

SUBDIRS = . $(BUILD_QT) $(BUILD_TEST)
DIST_SUBDIRS = . qt test
.PHONY: FORCE
# bitcoin core #
BITCOIN_CORE_H = \
  addrman.h \
  alert.h \
  allocators.h \
  base58.h \
  bignum.h \
  bitcoinrpc.h \
  bloom.h \
  checkpoints.h \
  checkqueue.h \
  coincontrol.h \
  clientversion.h \
  compat.h \
  crypter.h \
  db.h \
  genesis.h \
  hash.h \
  hashblock.h \
  init.h \
  kernel.h \
  key.h \
  keystore.h \
  limitedmap.h \
  lz4/lz4.h \
  main.h \
  miner.h \
  mruset.h \
  netbase.h \
  net.h \
  pbkdf2.h \
  pow_control.h \
  protocol.h \
  script.h \
  scrypt.h \
  serialize.h \
  sph_echo.h \
  sph_groestl.h \
  sph_jh.h \
  sph_keccak.h \
  sph_luffa.h \
  sph_shavite.h \
  sph_simd.h \
  sph_skein.h \
  sph_fugue.h \
  sph_hamsi.h \
  sph_types.h \
  sph_blake.h \
  sph_bmw.h \
  sph_cubehash.h \
  strlcpy.h \
  sync.h \
  threadsafety.h \
  txdb.h \
  txdb-leveldb.h \
  ui_interface.h \
  uint256.h \
  uint256_t.h \
  util.h \
  version.h \
  walletdb.h \
  wallet.h \
  xxhash/xxhash.h

if USE_SMESSAGE
BITCOIN_CORE_H += smessage.h
endif

JSON_H = \
  json/json_spirit.h \
  json/json_spirit_error_position.h \
  json/json_spirit_reader.h \
  json/json_spirit_reader_template.h \
  json/json_spirit_stream_reader.h \
  json/json_spirit_utils.h \
  json/json_spirit_value.h \
  json/json_spirit_writer.h \
  json/json_spirit_writer_template.h

obj/build.h: FORCE
	@$(MKDIR_P) $(abs_top_builddir)/src/obj
	@$(top_srcdir)/share/genbuild.sh $(abs_top_builddir)/src/obj/build.h \
	  $(abs_top_srcdir)
version.o: obj/build.h

libbitcoin_common_a_SOURCES = \
  addrman.cpp \
  alert.cpp \
  bitcoinrpc.cpp \
  bloom.cpp \
  checkpoints.cpp \
  crypter.cpp \
  db.cpp \
  hash.cpp \
  init.cpp \
  kernel.cpp \
  key.cpp \
  keystore.cpp \
  main.cpp \
  miner.cpp \
  netbase.cpp \
  net.cpp \
  noui.cpp \
  pbkdf2.cpp \
  protocol.cpp \
  rpcblockchain.cpp \
  rpcdump.cpp \
  rpcmining.cpp \
  rpcnet.cpp \
  rpcrawtransaction.cpp \
  rpcwallet.cpp \
  script.cpp \
  scrypt.cpp \
  sync.cpp \
  txdb-leveldb.cpp \
  util.cpp \
  version.cpp \
  wallet.cpp \
  walletdb.cpp \
  aes_helper.c \
  blake.c \
  bmw.c \
  cubehash.c \
  echo.c \
  groestl.c \
  jh.c \
  keccak.c \
  luffa.c \
  shavite.c \
  simd.c \
  skein.c \
  fugue.c \
  hamsi.c \
  xxhash/xxhash.c \
  $(JSON_H) \
  $(BITCOIN_CORE_H)

if USE_SMESSAGE
libbitcoin_common_a_SOURCES += \
  rpcsmessage.cpp \
  smessage.cpp
endif

libbitcoin_tor_a_SOURCES = \
 tor/address.c \
 tor/addressmap.c \
 tor/aes.c \
 tor/backtrace.c \
 tor/buffers.c \
 tor/channel.c \
 tor/channeltls.c \
 tor/circpathbias.c \
 tor/circuitbuild.c \
 tor/circuitlist.c \
 tor/circuitmux.c \
 tor/circuitmux_ewma.c \
 tor/circuitstats.c \
 tor/circuituse.c \
 tor/command.c \
 tor/compat.c \
 tor/compat_libevent.c \
 tor/config.c \
 tor/config_codedigest.c \
 tor/confparse.c \
 tor/connection.c \
 tor/connection_edge.c \
 tor/connection_or.c \
 tor/container.c \
 tor/control.c \
 tor/cpuworker.c \
 tor/crypto.c \
 tor/crypto_curve25519.c \
 tor/crypto_format.c \
 tor/curve25519-donna.c \
 tor/di_ops.c \
 tor/directory.c \
 tor/dirserv.c \
 tor/dirvote.c \
  tor/dns.c \
  tor/dnsserv.c \
  tor/entrynodes.c \
  tor/ext_orport.c \
  tor/fp_pair.c \
  tor/geoip.c \
  tor/hibernate.c \
  tor/log.c \
  tor/memarea.c \
  tor/mempool.c \
  tor/microdesc.c \
  tor/networkstatus.c \
  tor/nodelist.c \
  tor/onion.c \
  tor/onion_fast.c \
  tor/onion_main.c \
  tor/onion_ntor.c \
  tor/onion_tap.c \
  tor/policies.c \
  tor/anonymize.cpp \
  tor/procmon.c \
  tor/reasons.c \
  tor/relay.c \
  tor/rendclient.c \
  tor/rendcommon.c \
  tor/rendmid.c \
  tor/rendservice.c \
  tor/rephist.c \
  tor/replaycache.c \
  tor/router.c \
  tor/routerlist.c \
  tor/routerparse.c \
  tor/routerset.c \
  tor/sandbox.c \
  tor/statefile.c \
  tor/status.c \
  tor/strlcat.c \
  tor/strlcpy.c \
  tor/tor_util.c \
  tor/torgzip.c \
  tor/tortls.c \
  tor/transports.c \
  tor/util_codedigest.c

if GLIBC_BACK_COMPAT
libbitcoin_common_a_SOURCES += compat/glibc_compat.cpp
libbitcoin_common_a_SOURCES += compat/glibcxx_compat.cpp
endif

nodist_libbitcoin_common_a_SOURCES = $(top_srcdir)/src/obj/build.h
#

# bitcoind binary #
bitcoinplusd_LDADD = \
  libbitcoin_common.a \
  $(LIBLEVELDB) \
  $(LIBMEMENV)
if USE_TOR
bitcoinplusd_LDADD += libbitcoin_tor.a
endif
bitcoinplusd_SOURCES = bitcoind.cpp
#

if TARGET_WINDOWS
bitcoinplusd_SOURCES += bitcoind-res.rc
endif

AM_CPPFLAGS += $(BDB_CPPFLAGS)
bitcoinplusd_LDADD += $(BOOST_LIBS) $(BDB_LIBS)

# NOTE: This dependency is not strictly necessary, but without it make may try to build both in parallel, which breaks the LevelDB build system in a race
leveldb/libleveldb.a: leveldb/libmemenv.a

leveldb/%.a:
	@echo "Building LevelDB ..." && $(MAKE) -C $(@D) $(@F) CXX="$(CXX)" \
	  CC="$(CC)" PLATFORM=$(TARGET_OS) AR="$(AR)" $(LEVELDB_TARGET_FLAGS) \
	  OPT="$(CXXFLAGS) $(CPPFLAGS)"

CLEANFILES = leveldb/libleveldb.a leveldb/libmemenv.a *.gcda *.gcno

DISTCLEANFILES = obj/build.h

EXTRA_DIST = leveldb Makefile.include

clean-local:
	-$(MAKE) -C leveldb clean
	rm -f leveldb/*/*.gcno leveldb/helpers/memenv/*.gcno
