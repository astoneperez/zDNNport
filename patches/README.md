vector` keyword mapped to `__vector` for clang's AltiVec vector syntax
- Skip `.insn`-based `vec_float`/`vec_round` macros for clang (vecintrin.h provides these)
- Fix header guard mismatch (`ZDNN_ZDNN_PRIVATE_H` -> `ZDNN_ZDNN_PRIVATE_H_`)

**zdnn/zdnn_init.c** — Clang compatibility
- Guard XL C system headers (`cvt.h`, `ihaecvt.h`, `ihafacl.h`, `ihapsa.h`) from clang
- Add clang path for `zdnn_is_nnpa_installed()` using STFLE instead of CVT walk
- Add clang-specific `invoke_stfle()` using HLASM uppercase mnemonics
`__dcbtst`, `__dcbf` cache intrinsics (XL C only) from clang
- Fall back to `__builtin_prefetch` for clang

**zdnn/convert_hw.c** — Clang compatibility
- Replace `vector float` static initializers with `vec_float32` hex literals for clang
- Add clang asm paths using HLASM mnemonics (VCRNF, VCNF, VCLFNH, VCLFNL, VCFN)
- Replace `DC XL6'...'` inline asm with HLASM mnemonic equivalents
