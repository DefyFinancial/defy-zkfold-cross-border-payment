# Milestone 1

1. `KYCData` type is integrated into zkFold Symbolic framework. It is the main data type that will be used in descriptions of inter-banking requirements in this project. Now, we can create arbitrary statements about such data structures and verify them using ZKPs. See the link below
    
    [https://github.com/zkFold/zkfold-base/blob/main/symbolic-apps/src/ZkFold/Symbolic/Apps/KYC.hs](https://github.com/zkFold/zkfold-base/blob/main/symbolic-apps/src/ZkFold/Symbolic/Apps/KYC.hs)
    
    As a part of this output, we added support for JSON serialization/deserialization for zkFold Symbolic versions of bytestrings and unsigned integers, as well as for this new `KYCData` type.
    
2. We have completed the Plutus smart contract that will be used to mint a “KYC token” that proves the completion of a particular KYC verification procedure. See `plonkVerifierCompiled` here:
    
    [https://github.com/zkFold/zkfold-cardano/blob/main/src/ZkFold/Cardano/UPLC.hs](https://github.com/zkFold/zkfold-cardano/blob/main/src/ZkFold/Cardano/UPLC.hs)
    
    [https://github.com/zkFold/zkfold-cardano/blob/main/src/ZkFold/Cardano/UPLC/PlonkVerifier.hs](https://github.com/zkFold/zkfold-cardano/blob/main/src/ZkFold/Cardano/UPLC/PlonkVerifier.hs)
    
    All code related to the smart contract has been thoroughly tested and benchmarked. For details, see
    
    [https://github.com/zkFold/zkfold-base/blob/main/symbolic-base/test/Tests/NonInteractiveProof.hs](https://github.com/zkFold/zkfold-base/blob/main/symbolic-base/test/Tests/NonInteractiveProof.hs)
    
    [https://github.com/zkFold/zkfold-cardano/blob/main/test/Tests/Compatibility.hs](https://github.com/zkFold/zkfold-cardano/blob/main/test/Tests/Compatibility.hs)
    
    [https://github.com/zkFold/zkfold-cardano/blob/main/benchs/bench-cpu-mem/README.md](https://github.com/zkFold/zkfold-cardano/blob/main/benchs/bench-cpu-mem/README.md)
