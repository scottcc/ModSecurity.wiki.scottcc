# ModSecurity version 3 Release Candidate 1

This wikipage highlights some of the updates between the latest ModSecurity version 2, v3 earlier codebases and the released RC1.

This updated release candidate of libModSecurity is targeting the most widely used features from version 2. Its goal is to fully and correctly support common commercial and free rulesets such as "OWASP Core Rules Set version 3". We realize that many of the missing pieces have a very low audience, and they will continue to be targeted in the upcoming releases candidates. The updated list of missing pieces are listed in this wikipage.

## Connectors

The Nginx connector is being the de-facto setup to use and test libModSecurity. We've been having many feedbacks from the community and commercial users as well as contributions for this setup. A lot of effort have been put into it so far. For this reason we're also close to a release for the Nginx Connector.

https://github.com/SpiderLabs/ModSecurity-nginx

There have been a lot of work in the Apache connector as well, and this one is already available for testing but a RC release will take some more time until we finish polishing all the hard edges and get more feedback and contributions from the community.

https://github.com/SpiderLabs/ModSecurity-apache

## Code testing for robustness and maturity

Effort has also been put to testing the code extensively. As of now we have Regression tests, Unit tests (make check), Valgrind integration (--enable-valgrind) for checking memory leaks and more recently, Fuzzer testing. The fuzzer tests are individually testing each operator and transformation and in the future fuzzing tests will be expanded to the rules parser. The tests are based on American Fuzzy Lop (AFL) and they are available as part of configuration portion of compilation (--enable-afl-fuzz).

## Missing pieces (Towards version 3 feature complete).

The most important missing features belong to a milestone: Feature complete. 
This milestone can be listed here:  https://github.com/SpiderLabs/ModSecurity/milestone/9

Some other missing features are described on the reference manual by looking for the tag: Supported on libModSecurity: NO | TBI | TBD

If there's any specific feature that you are missing, please let us know by creating an issue on Github.

## What we don't want to support anymore

The list of unsupported features is still small at this point, although it may be bigger till the feature complete milestone. The single item is listed below.

- WEBSERVER_ERROR_LOG - https://github.com/SpiderLabs/ModSecurity/issues/1028
                      - https://github.com/SpiderLabs/ModSecurity/wiki/Reference-Manual#WEBSERVER_ERROR_LOG

- SecCacheTransformations - This was an experimental feature. Not much adoption so will be dropped for now.
                          - https://github.com/SpiderLabs/ModSecurity/wiki/Reference-Manual#SecCacheTransformations

- SecConnReadStateLimit - This directive is exclusive for Apache. As such it doest not belong on libModSecurity core code. Will be reimplemented on Apache Connector if need be.
                    - https://github.com/SpiderLabs/ModSecurity/wiki/Reference-Manual#SecCacheTransformations#SecConnReadStateLimit

- SecConnWriteStateLimit - This directive is exclusive for Apache. As such it doest not belong on libModSecurity core code. Will be reimplemented on Apache Connector if need be.
                    - https://github.com/SpiderLabs/ModSecurity/wiki/Reference-Manual#SecConnWriteStateLimit

- SecRequestBodyInMemoryLimit - https://github.com/SpiderLabs/ModSecurity/issues/1516 
                              - https://github.com/SpiderLabs/ModSecurity/wiki/Reference-Manual#SecRequestBodyInMemoryLimit

- SecStreamInBodyInspection - https://github.com/SpiderLabs/ModSecurity/issues/1316
                          - https://github.com/SpiderLabs/ModSecurity/wiki/Reference-Manual#SecStreamInBodyInspection

- STREAM_INPUT_BODY - https://github.com/SpiderLabs/ModSecurity/issues/1316
                          - https://github.com/SpiderLabs/ModSecurity/wiki/Reference-Manual#STREAM_INPUT_BODY

- SecGsbLookupDb - https://github.com/SpiderLabs/ModSecurity/issues/998
                 - https://github.com/SpiderLabs/ModSecurity/wiki/Reference-Manual#SecGsbLookupDb

- GsbLookup - https://github.com/SpiderLabs/ModSecurity/issues/998
            - https://github.com/SpiderLabs/ModSecurity/wiki/Reference-Manual#SecGsbLookupDb

