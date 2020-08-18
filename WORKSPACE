workspace(name = "libfqfft")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "rules_foreign_cc",
    strip_prefix="rules_foreign_cc-master",
    url = "https://github.com/bazelbuild/rules_foreign_cc/archive/master.zip",
)

load("@rules_foreign_cc//:workspace_definitions.bzl",
     "rules_foreign_cc_dependencies")
rules_foreign_cc_dependencies()

################################
##  Bazelized external repos  ##

# build target: @libff//libff
local_repository( name = "libff" , path = "depends/libff")
# http_archive(
#     name = "libff",
#     urls = ["https://github.com/obazl/libff/archive/bzl-1.0.tar.gz"],
#     # commit: 377e995d1a6cb6f0b250b79b3fb89291064a4c7b
#     strip_prefix = "libff-bzl-1.0",
#     # sha256 = "d280e666aa08cc2a458c034ece16c87861240e3c5b3cc727e902bd9ee0b19831"
# )

# not directly used, but contains build file for libgmp, aliased in //bzl/external/libgmp
local_repository( name = "ate_pairing" , path = "depends/ate-pairing")
# http_archive(
#     name = "ate_pairing",
#     urls = ["https://github.com/obazl/ate-pairing/archive/bzl-1.0.tar.gz"],
#     # commit: 8d34a92e92b0c661291dfc177f9e2b61c78597c4
#     strip_prefix = "ate-pairing-bzl-1.0",
#     sha256 = "e89a6a33eda28e93ae616b57ba5d4693f7b434b4d3407462caaab46a535d35ad"
# )

## not directly used, but needed by ate_pairing
local_repository( name = "xbyak" , path = "depends/xbyak")
# http_archive(
#     name = "xbyak",
#     urls = ["https://github.com/obazl/xbyak/archive/bzl-1.0.tar.gz"],
#     # commit: 89f7b734cb934518f12cb5836e6aca18f999172a
#     strip_prefix = "xbyak-bzl-1.0",
#     sha256 = "84fc1e7a73ec9077b05516422775ac90086ef45976aaf43f65368529cb71a75d"
# )

################################
# Non-bazelized external repos #

all_content = """filegroup(name = "all", srcs = glob(["**"]), visibility = ["//visibility:public"])"""

## openmp: build rule //bzl/external/openmp, alias for @libff//bzl/external/openmp
http_archive(
    name="openmp",
    url="https://github.com/llvm/llvm-project/releases/download/llvmorg-10.0.0/openmp-10.0.0.src.tar.xz",
    sha256="3b9ff29a45d0509a1e9667a0feb43538ef402ea8cfc7df3758a01f20df08adfa",
    strip_prefix="openmp-10.0.0.src",
    build_file_content = all_content
)

# openssl: used by libff, not libfqfft; built by @libff//bzl/external/openssl
http_archive(
    name="openssl",
    url="https://www.openssl.org/source/openssl-1.1.1g.tar.gz",
    sha256="ddb04774f1e32f0c49751e21b67216ac87852ceb056b75209af2443400636d46",
    strip_prefix="openssl-1.1.1g",
    build_file_content = all_content
)

## libgmp: built by @ate_pairing//bzl/external/libgmp, aliased in //bzl/external/libgmp
http_archive(
    name="libgmp",
    url="https://gmplib.org/download/gmp/gmp-6.2.0.tar.xz",
    sha256="258e6cd51b3fbdfc185c716d55f82c08aff57df0c6fbd143cf6ed561267a1526",
    strip_prefix = "gmp-6.2.0",
    build_file_content = all_content
)

http_archive(
    name="gtest",
    url="https://github.com/google/googletest/archive/release-1.10.0.tar.gz",
    sha256="9dc9157a9a1551ec7a7e43daea9a694a0bb5fb8bec81235d8a1e6ef64c716dcb",
    strip_prefix = "googletest-release-1.10.0",
)

# awaiting fix to gitlab bug
# http_archive(
#     name="libprocps",
#     url="https://gitlab.com/procps-ng/procps/-/archive/v3.3.16/procps-v3.3.16.tar.gz",
#     sha256="7f09945e73beac5b12e163a7ee4cae98bcdd9a505163b6a060756f462907ebbc",
#     strip_prefix = "procps-v3.3.16",
#     build_file = "@//external:libprocps.BUILD"
# )
