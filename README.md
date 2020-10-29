CHIPS Core integration/staging tree
=====================================

What is Chips?
----------------

CHIPS is a digital crypto currency which is used across all the gaming platforms 
designed and developed using the pangea protocol. CHIPS is a  BTC fork with an 
apow(adoptive proof of work) integration with a block time adjusted to less than 
10 seconds to suits to the needs of the betting in real time using CHIPS. Like BTC, 
CHIPS uses peer-to-peer technology to operate with no central authority: managing 
transactions and issuing money are carried out collectively by the network. CHIPS 
Core is the name of open source software which enables the use of this currency.

For more information, read the [original whitepaper](https://cdn.discordapp.com/attachments/455737840668770315/456036359870611457/Unsolicited_PANGEA_WP.pdf). <br/>
The first post about CHIPS by jl777 in [bitcointalk](https://bitcointalk.org/index.php?topic=2078449.0).

License
-------

CHIPS Core is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/licenses/MIT.

Development Process
-------------------

The `master` branch is regularly built and tested, but is not guaranteed to be
completely stable. [Tags](https://github.com/chips-blockchain/chips/tags) are created
regularly to indicate new official, stable release versions of Bitcoin Core.

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md).
### Useful links 
Steps to compile and run the chips node are mentioned in [COMPILE.md](/COMPILE.md). <br/>
Steps to generate the chips-qt wallet are mentioned in [CHIPS-QT.md](CHIPS-QT.md).

Testing
-------

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test on short notice. Please be patient and help out by testing
other people's pull requests, and remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write [unit tests](src/test/README.md) for new code, and to
submit new unit tests for old code. Unit tests can be compiled and run
(assuming they weren't disabled in configure) with: `make check`. Further details on running
and extending unit tests can be found in [/src/test/README.md](/src/test/README.md).

There are also [regression and integration tests](/test), written
in Python, that are run automatically on the build server.
These tests can be run (if the [test dependencies](/test) are installed) with: `test/functional/test_runner.py`

The Travis CI system makes sure that every pull request is built for Windows, Linux, and OS X, and that unit/sanity tests are run automatically.

### Manual Quality Assurance (QA) Testing

Changes should be tested by somebody other than the developer who wrote the
code. This is especially important for large or high-risk changes. It is useful
to add a test plan to the pull request description if testing the changes is
not straightforward.

CHIPS Community - Discord
-------------------------

We have an active [discord channel](https://discord.gg/tV7ADNE) where you can get to know more about CHIPS.

