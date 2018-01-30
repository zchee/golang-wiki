These are benchmarks collected from the community used to measure the effects of changes to the Go core (compiler, runtime, and libraries). They should have the following properties:

 - they matter; someone cares, perhaps in a dollars-and-cents way, that they run well
 - they are go-gettable and don't require customized steps for building the benchmark
 - they run under `go test -bench ...`
 - they run relatively quickly, ideally a single "run" takes less than a second (there should perhaps be a separate set of longer-running benchmarks)
 - their timings are not gratuitously noisy
 - they run cleanly in a restricted environment, such as a Docker or rkt container
 - they're not gratuitously redundant with other benchmarks already in the list; we don't need ten microbenchmarks of Go transcendental functions

Information for each benchmark includes (or should include):

 - a short name for the benchmark
 - the path to `go get` the benchmark
 - a regexp for the benchmark suite excluding individual benchmarks that might be noisy, long-running, or redundant
 - (ideally) a contact person for questions about the benchmarks 

 | short name | notes | go get path | benchmark regexp | contact |
 | ---------- | ----- | ----------- | ---------------- | ------- |
 | capnproto2 | | `zombiezen.com/go/capnproto2/` | `Benchmark(TextMovementBetweenSegments\|Growth_MultiSegment)` | |
 | ethereum_bitutil | | `github.com/ethereum/go-ethereum/common/bitutil` | `Benchmark(BaseTest2KB\|FastTest2KB\|Encoding4KBVerySparse)` | |
 | ethereum_core | | `github.com/ethereum/go-ethereum/core` | `BenchmarkChainRead_full_10k` | |
 | ethereum_corevm | | `github.com/ethereum/go-ethereum/core/vm` | `BenchmarkOpDiv128` | |
 | ethereum_ecies | | `github.com/ethereum/go-ethereum/crypto/ecies` | `BenchmarkGenSharedKeyP256` | |
 | ethereum_ethash | | `github.com/ethereum/go-ethereum/consensus/ethash` | `BenchmarkHashimotoLight` | |
 | ethereum_sha3 | | `github.com/ethereum/go-ethereum/crypto/sha3` | `BenchmarkSha3_224_MTU` | |
 | ethereum_storage | | `github.com/ethereum/go-ethereum/swarm/storage` | `BenchmarkJoin_8` | |
 | gonum_blas_native | | `gonum.org/v1/gonum/blas/gonum` | `Benchmark(DasumMediumUnitaryInc\|Dnrm2MediumPosInc)` | |
 | gonum_community | | `gonum.org/v1/gonum/graph/community/` | `BenchmarkLouvainDirectedMultiplex` | |
 | gonum_lapack_native | | `gonum.org/v1/gonum/lapack/gonum` | `BenchmarkDgeev/Circulant10` | |
 | gonum_mat | | `gonum.org/v1/gonum/mat` | `Benchmark(MulWorkspaceDense1000Hundredth\|ScaleVec10000Inc20)` | |
 | gonum_path | | `gonum.org/v1/gonum/graph/path/` | `Benchmark(AStarUndirectedmallWorld_10_2_2_2_Heur\|Dominators/nested_if_n256)` | |
 | gonum_topo | | `gonum.org/v1/gonum/graph/topo/` | `Benchmark(TarjanSCCGnp_1000_half\|TarjanSCCGnp_10_tenth)` | |
 | gonum_traverse | | `gonum.org/v1/gonum/graph/traverse/` | `BenchmarkWalkAllBreadthFirstGnp_(10\|1000)_tenth` | |
 | hugo_helpers | | `github.com/gohugoio/hugo/helpers` | `Benchmark(StripHTML\|ReaderContains)` | |
 | hugo_hugolib | | `github.com/gohugoio/hugo/hugolib` | `BenchmarkParsePage` | |
 | hugo_hugolib_sitebuilding | | `github.com/gohugoio/hugo/hugolib` | `BenchmarkSiteBuilding/YAML,num_pages=10,num_tags=10,tags_per_page=20,shortcodes,render-12` | |
 | k8s_api | | `k8s.io/kubernetes/pkg/api/testing` | `BenchmarkEncodeCodecFromInternalProtobuf` | |
 | minio | | `github.com/minio/minio/cmd` | `BenchmarkGetObject5MbFS` | |
 | semver | | `github.com/Masterminds/semver` | `BenchmarkValidateVersionTildeFail` | |
 | spexs2 | | `github.com/egonelbre/spexs2/_benchmark/` | `BenchmarkRun/10k/1` | |
 | uuid | | `github.com/satori/go.uuid/` | `Benchmark(NewV5\|MarshalToString)` | |

There is a [benchmark runner](https://github.com/dr2chase/bent) that automates downloading, building, and running these benchmarks under various (user-defined) configurations.  Benchmarking noise on Linux can be somewhat reduced with [perflock](https://github.com/aclements/perflock).

A few have been proposed but have so far failed to make the cut (for fetch, build, or noise problems):

 | short name | notes | go get path | benchmark regexp | contact |
 | ---------- | ----- | ----------- | ---------------- | ------- |
 | eolian_dsp | | `buddin.us/eolian/dsp` | `Benchmark` | |
 | ethereum_trie | | `github.com/ethereum/go-ethereum/trie` | `Benchmark` | |
 | ethereum_whisperv5 | | `github.com/ethereum/go-ethereum/whisper/whisperv5` | `Benchmark` | |
 | k8s_schedulercache | | `k8s.io/kubernetes/plugin/pkg/scheduler/schedulercache` | `Benchmark` | |
 | kanzi | | `github.com/flanglet/kanzi/go/src/kanzi/benchmark` | `Benchmark` | |
 | uber_zap | | `github.com/uber-go/zap/benchmarks` | `Benchmark` | |
