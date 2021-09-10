version: 2
jobs:
  build:
    docker:
      - image: circleci/ruby:2.4.1
    steps:
      - checkout
      - run: echo "A first hello"
      - run: sleep 5
  test:
    docker:
      - image: circleci/ruby:2.4.1
    steps:
      - checkout
      - run: echo "A more familiar hi"
      - run: sleep 5
workflows:
  version: 2
  build_and_test:
    jobs:
      - build
      - test:
          # only run this job if build succeeds
          requires:
            - build 
