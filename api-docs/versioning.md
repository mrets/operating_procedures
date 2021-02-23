# Versioning

The M-RETS API will be managed using standard semantic versioning. When possible, we have tried to follow (this spec)[https://semver.org/].

The major version number will be embedded in the URL and the full version can be found in the header. M-RETS will only support one minor/patch version at any time. At the point we introduce a new major version, we commit to communicating well in advance of the changes and will continue to support an old major version for a set period of time also communicated well in advance to all API users.

All API minor and major changes will be posted in our API docs as well as sent out to our API email list. To join our list, sign-up here. 

## Breaking Changes

The M-RETS is a rapidly changing platform. In our design of the public facing API as well as in our management process, we have strived to balance our need to keep the platform flexible and dynamic while also providing a stable interface for 3rd party developers. In order to support both goals, we've tried to clearly define what we consider major and minor changes. Minor changes will not be considered backwards incompatible and users will be given one to two weeks notice of these changes. We hope by clearly setting these expectations of how we intend to manage the API, we can support our users in creating more maintainable integrations. 

| Change Description                                            | Classification of Change              |
|---------------------------------------------------------------|---------------------------------------|
| Add a new endpoint/entity                                     | Minor Version Change                  |
| Add a new (non-required) field to an existing entity/endpoint | Minor Version Change                  |
| Remove or rename an existing field                            | Major Version Change                  |
| Stop updating/using an existing field                         | Minor Version Change                  |
| Adding additional validations to existing fields              | Will evaluate on a case-by-case basis |
| Bug fixes                                                     | Patch Version Change                  |

Minor changes will deployed to our sandbox environment along with updated documentation 2 weeks in advance of the changes being pushed to prod. An email notification will go out information users exactly what will change as well as the anticipated release date. The intention is that these changes should not be backwards incompatible, but we want to give our users an opportunity to test their integrations before they go live.

Major changes will (hopefully) occure on a very infrequent basis. It is our intention to communicate clearly about the release of a new major version 2-3 months in advance of the major version going live. It is our intention to continue supporting a legacy major version for a minimum of 6 months after a new major version is available. 
