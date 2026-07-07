# Standalone PR Candidates

Based on recent branches (`guru/*`), the following commits contain isolated, clear fixes that are excellent candidates for standalone Pull Requests:

### 1. Clippy Warnings Fix (`guru/fix/unsafe-wbwi-pointer-ub`)

**Commit:** `5a1dd29`
This commit fixes a handful of `clippy::perf` and `clippy::pedantic` warnings. For example, it updates the code to use `std::ptr::from_ref` instead of casting an `Arc` reference, and fixes `try_from` vs `as usize` casts for improved safety.

- **Suggested Branch Name:** `guru/fix/clippy-pedantic-warnings`

### 2. Flaky Bulkload Test Fix (`guru/fix/unsafe-wbwi-pointer-ub`)

**Commits:** `2eff3f2` and `596b1c5` (or `dc14034` depending on the final version)
These commits set `max_subcompactions=1` and `target_file_size_base` to prevent the `get_with_cache_and_bulkload_test` from flaking (especially visible on ARM CI). Because these changes only tweak test parameters to ensure CI reliability, they are great standalone PR candidates.

- **Suggested Branch Name:** `guru/fix/flaky-bulkload-test`

### 3. Infer System Include Directory (`guru/perf/precompiles-option`)

**Commit:** `c93ba0d`
This improves the build script's logic. When `ROCKSDB_LIB_DIR` is set but `ROCKSDB_INCLUDE_DIR` is not, it automatically checks if a `../include` directory exists relative to the library directory. This is a very useful quality-of-life improvement for users linking against a system RocksDB.

- **Suggested Branch Name:** `guru/feat/infer-system-include-dir`

### 4. Backwards Compatibility for RocksDB v10 (`guru/backward-compat-v10`)

**Commit:** `32ab0b9`
This branch currently contains a single commit: `fix(sys): conditionally compile new features based on rocksdb version to support rocksdb 10`. Assuming it is tested and ready, this commit is perfectly isolated and ready for its own PR.

- **Suggested Branch Name:** `guru/backward-compat-v10` (or `guru/feat/support-rocksdb-v10`)
