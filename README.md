Dovecot logs grok patterns and logstash configuration
====================================================

Usage
-----

- Install logstash
- Add `dovecot.conf` to `/etc/logstash/conf.d`
- Add `dovecot.grok` to `/etc/logstash/dovecot.d`
- Either configure pipelines in a way consistent with `dovecot.conf` or override its `input` and `output` blocks in a way that suits your needs.
- Restart logstash

Tests
-----

This repository includes a test suite to ensure no regression is made when changing patterns to accomodate new log formats. It makes use of a script from the [postfix grok patterns repository](https://github.com/whyscream/postfix-grok-patterns) that requires `ruby 2.2` and the `jls-grok` and `minitest` gems. You also need to pull submodules (`git submodule update --init`).

Once everything is setup, you can simply add new tests case as yaml files in the test directory and execute the suite with `ruby test/test.rb`.

Contributing
------------
If your log format is not well-understood by this script (especially if it generates a `_dovecot_grok_nomatch` tag), you are welcome to send me a pull request including the necessary changes. Please mind to include at least an example in the `test` directory so that it can be resiliently included.


Acknowledgement
---------------
This repository is obviously deeply inspired by the fantastic [postfix grok patterns repository](https://github.com/whyscream/postfix-grok-patterns) from [whyscream](https://github.com/whyscream). The test script is also from him.
