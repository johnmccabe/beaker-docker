# Beaker Docker Container

**WIP** Does not include steps to automate test invocation at this point.

```
docker run -ti -v ~/.ssh/keys/vmpooler_priv:/vmpooler.priv -v ~/workspaces/your_tests/:/tests -v ~/.fog:/root/.fog -name beaker johnmccabe/beaker /bin/sh

cd /tests
export BUNDLE_PATH=/gems
export BUNDLE_GEMFILE=/gemfile/Gemfile
ln -s /tests/Gemfile /gemfile/Gemfile
bundle install
bundle exec beaker --xml --debug --root-keys --repo-proxy --preserve-hosts onfail --config hosts.cfg --type pe --keyfile /vmpooler.priv --tests mysuite/tests --helper lib/beaker_helper.rb --pre-suite setup/install.rb
```
