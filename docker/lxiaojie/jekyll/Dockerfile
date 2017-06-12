FROM jekyll/jekyll

RUN gem sources --add https://gems.ruby-china.org/ --remove https://rubygems.org/
RUN bundle config mirror.https://rubygems.org https://gems.ruby-china.org

RUN gem install

CMD bundle exec jekyll serve
