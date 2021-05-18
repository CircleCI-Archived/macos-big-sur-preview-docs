# macOS Big Sur Preview Documentation

The purpose of this repository is to walk you through the details of the macOS Big Sur preview on CircleCI.

**Note:** macOS Big Sur is available to existing CircleCI customers only. You must have signed up for a CircleCI Performance, Scale, or Custom plan before 26 Apr 2021. To get access to the macOS Big Sur preview as an existing customer, **fill out the [macOS Big Sur interest form](https://form.asana.com?k=vQFaJZp5XfPypEJ2S6O9KA&d=5374345383152)**.

## What are macOS Big Sur resources on CircleCI?

CircleCI offers a [macOS executor](https://circleci.com/docs/2.0/testing-ios/) that you can use to build and test macOS, iOS, watchOS, and tvOS applications. We support multiple Xcode versions through [macOS executor images](https://circleci.com/docs/2.0/testing-ios/#supported-xcode-versions).

macOS Big Sur is the latest image for the macOS executor that’s now available in preview on the next generation macOS infrastructure.

The identifier of the Big Sur image is `12.5.0` and the identifier for the Big Sur resource is `m2.medium`. The Big Sur resource can only be used with a Big Sur macOS image, and vice versa.

## Pricing and availability

The following macOS Big Sur resource class is available:

|Resource class name|Specs|Plans on which the resource is available|
|---|---|---|
|`m2.medium`|4 vCPUs, 8GB RAM | Performance, Scale, Custom|

## Getting access to the macOS Big Sur resources

To get access, **fill out the [macOS Big Sur interest form](https://form.asana.com?k=vQFaJZp5XfPypEJ2S6O9KA&d=5374345383152)**.

Requirements to get access to the macOS Big Sur preview:

* Your organization must be an existing CircleCI customer, and you must have signed up for a Performance, Scale, or Custom plan earlier than 22 Mar 2021.
    * For new customers, we are planning on offering macOS Big Sur resources later in 2021.

## Example of a CircleCI config using macOS Big Sur resources

```yaml
# .circleci/config.yml
version: 2.1
jobs:
  build-and-test:
    macos:
      # reference the Big Sur + Xcode 12.5 preview image
      xcode: 12.5.0
    # use the Big Sur preview resource class
    resource_class: m2.medium
    environment:
      FL_OUTPUT_DIR: output
      FASTLANE_LANE: test
    steps:
      - checkout
      - run: bundle install
      - run:
          name: Fastlane
          command: bundle exec fastlane $FASTLANE_LANE
      - store_artifacts:
          path: output
      - store_test_results:
          path: output/scan

workflows:
  build-test:
    jobs:
      - build-and-test
```

## How to provide feedback

Please [open an issue](https://github.com/CircleCI-Public/macos-big-sur-preview-docs/issues) with any feedback. The specific area where we would appreciate feedback:

* Software pre-installed in the image. Do you find everything you need in the image? Are there any bugs that you’ve noticed in the pre-installed software or operating system configuration?

Here is a link to the [**macOS Big Sur interest form**](https://form.asana.com?k=vQFaJZp5XfPypEJ2S6O9KA&d=5374345383152) again, just in case.
