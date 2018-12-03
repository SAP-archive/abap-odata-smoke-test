# Purpose

ODATA services nowadays serve as a foundation of SAP Fiori apps. This ABAP Report provides sample code to run simple ODATA smoke tests in order to check their technical availability after activation.

Flow:
* Evaluates all activated ODATA Services (as in transaction /IWFND/MAINT_SERVICE)
* Performs a $metadata call
* (Optional) Performs a service document call
* (Optional) Performs an arbitary entityset call
* Collects HTTP Status Codes / Response via SAP Application log

# Output

Once finished, results will be shown automatically! Moreover, they can also be observed via transaction "SLG1", Object "/IWFND/", Subobject "RUNTIME", as seen below. The result list can easily be sorted and help during further troubleshooting.

![demo smoke test](https://github.com/SAP/abap-odata-smoke-test/blob/master/docs/img/smoke_test.png)

# System Requirements

* tested on NW ABAP >= 7.52
* Requires working GW Client functionality (uses HTTP) - check also transaction "/IWFND/GW_CLIENT"
* User with SAP_ALL or similar authorizations to execute ODATA services and perform entityset calls

# Deployment

* Run transaction "SE38"
* create new executable report e.g. Z_ODATA_SMOKE_TEST
* [Copy & Paste Source Code](https://github.com/SAP/abap-odata-smoke-test/blob/master/src/Z_ODATA_SMOKE_TEST.txt)
* Save & Activate

# Execution

After deployment, run report via "SE38".

Output will be displayed automatically, once report is finished, or can be observed via transaction "SLG1", Object "/IWFND/", Subobject "RUNTIME".

Flag <test_entity = abap_false.> determines, whether entityset calls are performed (default = off).

> ATTENTION: Depending on the amount of active services, especially the initial execution can take minutes up to couple of hours!

# License

Copyright (c) 2018 SAP SE or an SAP affiliate company. All rights reserved.

The content of this repository is licensed under the SAP SAMPLE CODE LICENSE AGREEMENT as noted in the [LICENSE](https://github.com/SAP/abap-odata-smoke-test/blob/master/LICENSE) file.
