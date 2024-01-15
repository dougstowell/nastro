---
title: 'CI Build'
pubDate: 2021-07-01 15:00:00
description: 'CI Build'
author: 'Doug Stowell'
authorAvatar: '/src/assets/dougs.jpg'
image:
    url: '/src/assets/cicd.png'
    alt: 'CI Build'
tags: ["shell", "spine", "ci", "cd"]
isPinned: true
---

## Spine Specific.

```text
# Useful

/opt/vfm/spine_management.sh restart messageexchange*
/opt/vfm/spine_management.sh restart meshnotification*
/opt/vfm/spine_management.sh restart outbound_message_exchange*
/opt/vfm/spine_management.sh restart gp_links*
/opt/vfm/spine_management.sh restart prpa_in160000uk30*
/opt/vfm/spine_management.sh restart prpa_in000204uk03*
/opt/vfm/spine_management.sh restart prpa_in000204sm13*
/opt/vfm/spine_batch_management.sh restart gpLinks*

# alias swic and sglo
/opt/vfm/spine_batch_management.sh restart workitemconsumer*
/opt/vfm//spine_singleton_management.sh restart gp_links_outbound*

/opt/vfm/spine_singleton_management.sh restart gp_links_outbound_sequence_number
/opt/vfm/spine_singleton_management.sh restart gp_links_outbound_sequence_number_shovel
/opt/vfm/spine_management.sh restart proxyrequesthandler_instance1

sudo rm -rf /opt/vfm/log/output/*/*

sudo rm -r /opt/vfm/log/output/*/* && cd /home/spineii-user/spineii/dev/spinecore/build && ./ci-build.sh -stupiDjGl -S PRESCRIPTIONS -S INTERNETGATEWAY -S SINGLETON -S CLINICALS -S BATCH
sudo rm -r /opt/vfm/log/output/*/* && cd /home/spineii-user/spineii/dev/spinecore/build && ./ci-build.sh -stupiDjGlod -S PRESCRIPTIONS -S INTERNETGATEWAY -S SINGLETON -S CLINICALS -S BATCH

cd /home/spineii-user/spineii/dev/spinecore/build && ./ci-build.sh -stupiDjGlod -S PRESCRIPTIONS -S INTERNETGATEWAY -S SINGLETON -S CLINICALS -S BATCH

# List spine services
/opt/vfm/spine_management.sh list
/opt/vfm/spine_management.sh running
/opt/vfm/spine_management.sh stopped

# E.g. starting service
/opt/vfm/spine_management.sh start meshnotification_w1
/opt/vfm/spine_management.sh start messageexchange*
/opt/vfm/spine_management.sh start ipsosMORIGPPracticeSurveyWorker_w1
/opt/vfm/spine_management.sh start outbound_message_exchange_w1

/opt/vfm/spine_management.sh restart ipsosMORIGPPracticeSurveyWorker_w1
/opt/vfm/spine_management.sh gracefulrestart ipsosMORIGPPracticeSurveyWorker_w1

/opt/vfm/spine_singleton_management.sh stopped | grep sar
/opt/vfm/spine_singleton_management.sh gracefulrestart sar_logharvest_orchestrator

# ALLOCATING PATIENTS!
/opt/vfm/spine_management.sh start numberAllocation_w1

# Batch service  management
/opt/vfm/spine_batch_management.sh running
/opt/vfm/spine_batch_management.sh gracefulrestart demographicCohortDeltaUpdateSender
/opt/vfm/spine_batch_management.sh start workitemconsumer
/opt/vfm/spine_batch_management.sh stop workitemconsumer
/opt/vfm/spine_batch_management.sh running | grep workitemconsumer

/opt/vfm/spine_batch_management.sh list | grep wiprocessingtimereport

/opt/vfm/spine_batch_management.sh list | grep asct

# Web service  management
/opt/vfm/spine_webservices_management.sh running
/opt/vfm/spine_webservices_management.sh gracefulrestart spinereportingservice
/opt/vfm/spine_webservices_management.sh gracefulrestart spinereportingservice_rest-instance1

/opt/vfm/spine_webservices_management.sh stop demographicspineapplication
/opt/vfm/spine_webservices_management.sh stop demographicspineapplication_rest-instance1

# RELOAD TEST DATA?
./dev/spinecore/build/ci-load-test-data.sh -a 1 2 3

```
