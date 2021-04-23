<html>
<p align="center"> 
  <img src="rsts/images/flyte-and-lf.png" alt="Flyte and LF AI & Data Logo" width="300">
</p>

<h1 align="center">
  Flyte
</h1>

<p align="center">
Flyte is a <b>production-grade</b>, <b>container-native</b>, <b>type-safe workflow and pipelines platform</b> optimized for large scale processing and machine learning, written in Golang.
</p>

<p align="center">
  <a href="https://github.com/lyft/flyte/releases/latest">
    <img src="https://img.shields.io/github/release/lyft/flyte.svg" alt="Current Release" />
  </a>
  <a href="https://github.com/flyteorg/flyte/actions/workflows/sandbox.yml">
    <img src="https://github.com/flyteorg/flyte/actions/workflows/sandbox.yml/badge.svg" alt="Sandbox Build" />
  </a>
  <a href="https://github.com/flyteorg/flyte/actions/workflows/tests.yml">
    <img src="https://github.com/flyteorg/flyte/actions/workflows/tests.yml/badge.svg" alt="End-to-End Tests" />
  </a>
  <a href="http://www.apache.org/licenses/LICENSE-2.0.html">
    <img src="https://img.shields.io/badge/LICENSE-Apache2.0-ff69b4.svg" alt="License" />
  </a>
  <img src="https://img.shields.io/github/commit-activity/w/lyft/flyte.svg?style=plastic" alt="Commit Activity" />
  <img src="https://img.shields.io/github/commits-since/lyft/flyte/latest.svg?style=plastic" alt="Commits since Last Release" />
  <img src="https://img.shields.io/github/milestones/closed/lyft/flyte?style=plastic" alt="GitHub Milestones Completed" />
  <img src="https://img.shields.io/github/milestones/progress-percent/lyft/flyte/11?style=plastic" alt="GitHub Next Milestone Percentage" />
  <a href="https://flyte.rtfd.io">
    <img src="https://readthedocs.org/projects/flyte/badge/?version=latest&style=plastic" alt="Docs" />
  </a>
  <img src="https://img.shields.io/twitter/follow/flyteorg?label=Follow&style=social" alt="Twitter Follow" />
  <a href="https://forms.gle/UVuek9WfBoweiqcJA">
    <img src="https://img.shields.io/badge/slack-join_chat-white.svg?logo=slack&style=social" alt="Slack Status" />
  </a>
</p>

<h3 align="center">
  <a href="https://flyte.org">Home Page</a>
  <span> · </span>
  <a href="#quickstart">Quick Start</a>
  <span> · </span>
  <a href="https://docs.flyte.org/">Documentation</a>
  <span> · </span>
  <a href="#features">Features</a>
  <span> · </span>
  <a href="#community--resources">Community & Resources</a>
  <span> · </span>
  <a href="CHANGELOG/">Changelogs</a>
  <span> · </span>  
  <a href="#component-repos">Components</a>
</h3>

</html>

## 💥 Introduction

Flyte is a structured programming and distributed processing platform that enables highly concurrent, scalable and maintainable workflows for `Machine Learning` and `Data Processing`. It is a fabric that connects disparate computation backends using a type safe data dependency graph. It records all changes to a pipeline, making it possible to rewind time. It also stores
a history of all executions and provides an intuitive UI, CLI and REST/gRPC API to interact with the computation.

Flyte is more than a workflow engine -- `workflow` is the core concept, and a single unit of execution is called a `task` as a top level concept. Multiple tasks arranged in a data producer-consumer order create a workflow.

`Workflows` and `Tasks` can be written in any language, with out of the box support for [Python](https://github.com/flyteorg/flytekit), [Java and Scala](https://github.com/spotify/flytekit-java).

<html>
<h2 id="quickstart"> 
  🚀 Quick Start
</h2>
</html>

With [docker installed](https://docs.docker.com/get-docker/), run the following command:

```bash
  docker run --rm --privileged -p 30081:30081 -p 30084:30084 ghcr.io/flyteorg/flyte-sandbox
```

This creates a local Flyte sandbox. Once the sandbox is ready, you should see the following message: `Flyte is ready! Flyte UI is available at http://localhost:30081/console`.

Go ahead and visit http://localhost:30081/console to view the Flyte dashboard.

Here's a quick visual tour of the console.

![Flyte console Example](https://github.com/flyteorg/flyte/raw/static-resources/img/first-run-console-2.gif)

To dig deeper into Flyte, refer to the [Documentation](https://docs.flyte.org/en/latest/index.html).

## ⭐️ Current Deployments

- [Freenome](https://www.freenome.com/)
- [Lyft Rideshare, Mapping](https://www.lyft.com/)
- [Lyft L5 autonomous](https://self-driving.lyft.com/level5/)
- [Spotify](https://www.spotify.com/)
- [USU Group](https://www.usu.com/)
- [Striveworks](https://striveworks.us/)

<html>
<h2 id="features"> 
  🔥 Features
</h2>
</html>

- Used at _Scale_ in production by **500+** users at Lyft with more than **1 million** executions and **40+ million** container executions per month
- Enables **collaboration across your organization**, to:
  - Execute distributed data pipelines/workflows
  - Reuse tasks across projects, users, and workflows
  - Backtrack to a specified workflow
  - Compare results of training workflows over time and across pipelines
  - Share workflows and tasks across your teams
- **[Quick registration](https://docs.flyte.org/projects/cookbook/en/latest/tutorial.html)** -- start locally and scale to the cloud instantly
- **Centralized Inventory** constituting of Tasks, Workflows and Executions
- **gRPC / REST** interface to define and execute tasks and workflows
- **Type safe** construction of pipelines -- each task has an interface which is characterized by its input and output. Illegal construction of pipelines therefore fails during declaration rather than at runtime
- Supports multiple **[data types](https://docs.flyte.org/projects/cookbook/en/latest/core.html)** for machine learning and data processing pipelines, such as Blobs (images, arbitrary files), Directories, Schema (columnar structured data), collections, maps etc.
- Memoization and Lineage tracking
- Workflow features:
  - Start with one task, convert to a pipeline, attach **[multiple schedules](https://docs.flyte.org/projects/cookbook/en/latest/auto_core_remote_flyte/lp_schedules.html)**, trigger using a programmatic API, or on-demand
  - Parallel step execution
  - Extensible backend to add [customized plugin](https://docs.flyte.org/projects/cookbook/en/latest/auto_core_advanced/custom_task_plugin.html) experience (with simplified user experience)
  - **[Branching](https://docs.flyte.org/projects/cookbook/en/latest/auto_core_intermediate/run_conditions.html)**
  - Inline **[subworkflows](https://docs.flyte.org/projects/cookbook/en/latest/auto_core_intermediate/subworkflows.html)** (a workflow can be embeded within one node of the top level workflow)
  - Distributed **remote child workflows** (a remote workflow can be triggered and statically verified at compile time)
  - **[Array Tasks](https://docs.flyte.org/projects/cookbook/en/latest/auto_core_intermediate/map_task.html)** (map a function over a large dataset -- ensures controlled execution of thousands of containers)
  - **[Dynamic workflow](https://docs.flyte.org/projects/cookbook/en/latest/auto_core_intermediate/dynamics.html)** creation and execution with runtime type safety
  - Container side [plugins](https://docs.flyte.org/projects/cookbook/en/latest/plugins.html) with first class support in Python
  - _PreAlpha_: Arbitrary flytekit-less containers supported ([RawContainer](https://docs.flyte.org/projects/cookbook/en/latest/auto_core_intermediate/raw_container.html))
- Guaranteed **[reproducibility](https://docs.flyte.org/projects/cookbook/en/latest/auto_core_basic/task_cache.html)** of pipelines via:
  - Versioned data, code and models
  - Automatically tracked executions
  - Declarative pipelines
- **Multi cloud support** (AWS, GCP and others)
- Extensible core, modularized, and deep observability
- Automated notifications to Slack, Email, and Pagerduty
- [Multi K8s cluster support](https://docs.flyte.org/projects/cookbook/en/latest/auto_plugins_pod/index.html)
- Out of the box support to run **[Spark jobs on K8s](https://docs.flyte.org/projects/cookbook/en/latest/auto_plugins_k8s_spark/index.html)**, **[Hive queries](https://docs.flyte.org/projects/cookbook/en/latest/auto_plugins_hive/index.html)**, etc.
- Snappy Console
- Python CLI and Golang CLI (flytectl)
- Written in **Golang** and optimized for large running jobs' performance

### In Progress

- Grafana templates (user/system observability)
- Helm chart for Flyte
- Performance optimization
- Flink-K8s

## 🔌 Available Plugins

- Containers
- [K8s Pods](https://docs.flyte.org/projects/cookbook/en/latest/auto_plugins_pod/index.html)
- AWS Batch Arrays
- K8s Pod Arrays
- K8s Spark (native [Pyspark](https://docs.flyte.org/projects/cookbook/en/latest/auto_plugins_k8s_spark/index.html) and Java/Scala)
- AWS Athena
- [Qubole Hive](https://docs.flyte.org/projects/cookbook/en/latest/auto_plugins_hive/index.html)
- Presto Queries
- Distributed Pytorch (K8s Native) -- [Pytorch Operator](https://docs.flyte.org/projects/cookbook/en/latest/auto_plugins_kfpytorch/index.html)
- Sagemaker ([builtin algorithms](https://docs.flyte.org/projects/cookbook/en/latest/auto_plugins_sagemaker_training/sagemaker_builtin_algo_training.html) & [custom models](https://docs.flyte.org/projects/cookbook/en/latest/auto_plugins_sagemaker_training/sagemaker_custom_training.html))
- Distributed Tensorflow (K8s Native) - TFOperator
- Papermill notebook execution ([Python](https://github.com/lyft/flytekit/tree/master/plugins/papermill) and Spark)
- Type safe and data checking for Pandas dataframe using Pandera

### In Queue

- Reactive pipelines
- A lot more integrations!

<html>
<h2 id="component-repos"> 
  📦 Component Repos 
</h2>
</html>

| Repo                                                      | Language      | Purpose                                        | Status           |
| --------------------------------------------------------- | ------------- | ---------------------------------------------- | ---------------- |
| [flyte](https://github.com/lyft/flyte)                    | Kustomize,RST | deployment, documentation, issues              | Production-grade |
| [flyteidl](https://github.com/lyft/flyteidl)              | Protobuf      | interface definitions                          | Production-grade |
| [flytepropeller](https://github.com/lyft/flytepropeller)  | Go            | execution engine                               | Production-grade |
| [flyteadmin](https://github.com/lyft/flyteadmin)          | Go            | control plane                                  | Production-grade |
| [flytekit](https://github.com/lyft/flytekit)              | Python        | python SDK and tools                           | Production-grade |
| [flyteconsole](https://github.com/lyft/flyteconsole)      | Typescript    | admin console                                  | Production-grade |
| [datacatalog](https://github.com/lyft/datacatalog)        | Go            | manage input & output artifacts                | Production-grade |
| [flyteplugins](https://github.com/lyft/flyteplugins)      | Go            | flyte plugins                                  | Production-grade |
| [flytestdlib](https://github.com/lyft/flytestdlib)        | Go            | standard library                               | Production-grade |
| [flytesnacks](https://github.com/lyft/flytesnacks)        | Python        | examples, tips, and tricks                     | Incubating       |
| [flytekit-java](https://github.com/spotify/flytekit-java) | Java/Scala    | Java & scala SDK for authoring Flyte workflows | Incubating       |
| [flytectl](https://github.com/lyft/flytectl)              | Go            | A standalone Flyte CLI                         | Incomplete       |

## 🔩 Production K8s Operators

| Repo                                                                  | Language | Purpose                |
| --------------------------------------------------------------------- | -------- | ---------------------- |
| [Spark](https://github.com/GoogleCloudPlatform/spark-on-k8s-operator) | Go       | Apache Spark batch     |
| [Flink](https://github.com/lyft/flinkk8soperator)                     | Go       | Apache Flink streaming |

<html>
<h2 id="community--resources"> 
  🤝 Community & Resources
</h2>
</html>

Here are some resources that would help you better understand Flyte.

| Community Resources         |                                                                                                                                                                                                                                                                                        |
|-----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Community Channels**      | [Slack Org](https://forms.gle/UVuek9WfBoweiqcJA)                                                                                                                                                                                                                                       |
|                             | [Email list](https://groups.google.com/a/flyte.org/g/users)                                                                                                                                                                                                                            |
| **Biweekly Community Sync** | Flyte OSS Community Sync, every other Tuesday, 9am-10am PDT                                                                                                                                                                                                                            |
|                             | [Events calendar & Sign Up](https://calendar.google.com/calendar/embed?src=admin%40flyte.org&ctz=America%2FLos_Angeles)                                                                                                                                                                |
|                             | [Zoom link](https://us04web.zoom.us/j/71298741279?pwd=TDR1RUppQmxGaDRFdzBOa2lHN1dsZz09)                                                                                                                                                                                                |
|                             | Meeting notes and topics are captured in this [document](https://docs.google.com/document/d/1Jb6eOPOzvTaHjtPEVy7OR2O5qK1MhEs3vv56DX2dacM/edit#heading=h.c5ha25xc546e)                                                                                                                  |
|                             | Previous meeting [video recordings](https://www.youtube.com/channel/UCNduEoLOToNo3nFVly-vUTQ)                                                                                                                                                                                          |
| **Blog Posts**              | [Introducing Flyte: A Cloud Native Machine Learning and Data Processing Platform](https://eng.lyft.com/introducing-flyte-cloud-native-machine-learning-and-data-processing-platform-fb2bb3046a59)                                                                                      |
|                             | [Building a Gateway to Flyte](https://eng.lyft.com/building-a-gateway-to-flyte-474b451b32c8)                                                                                                                                                                                           |
| **Podcasts**                | TWIML&AI -  [Scalable and Maintainable ML Workflows at Lyft - Flyte](https://twimlai.com/twiml-talk-343-scalable-and-maintainable-workflows-at-lyft-with-flyte-w-haytham-abuelfutuh-and-ketan-umare/)                                                                                  |
|                             | Software Engineering Daily - [Flyte: Lyft Data Processing Platform](https://softwareengineeringdaily.com/2020/03/12/flyte-lyft-data-processing-platform-with-allyson-gale-and-ketan-umare/)                                                                                            |
|                             | MLOps Coffee session - [Flyte: an open-source tool for scalable, extensible, and portable workflows](https://anchor.fm/mlops/episodes/MLOps-Coffee-Sessions-12-Flyte-an-open-source-tool-for-scalable--extensible---and-portable-workflows-eksa5k)                                     |
| **Conference Talks**        | Kubecon 2019 - Flyte: Cloud Native Machine Learning and Data Processing Platform  [video](https://www.youtube.com/watch?v=KdUJGSP1h9U) [deck](https://kccncna19.sched.com/event/UaYY/flyte-cloud-native-machine-learning-data-processing-platform-ketan-umare-haytham-abuelfutuh-lyft) |
|                             | Kubecon 2019 - Running LargeScale Stateful workloads on Kubernetes at Lyft [video](https://www.youtube.com/watch?v=ECeVQoble0g)                                                                                                                                                        |
|                             | re:invent 2019 - Implementing ML workflows with Kubernetes and Amazon Sagemaker [video](https://youtu.be/G-wzIQQJKaE)                                                                                                                                                                  |
|                             | Cloud-native machine learning at Lyft with AWS Batch and Amazon EKS [video](https://youtu.be/n_rRb8u1GSM)                                                                                                                                                                              |
|                             | OSS + ELC NA 2020 [splash](https://ossna2020.sched.com/event/313cec91aa38a430a25f9571039874b8)                                                                                                                                                                                         |
|                             | Datacouncil [splash](https://docs.google.com/document/d/1ZsCDOZ5ZJBPWzCNc45FhNtYQOxYHz0PAu9lrtDVnUpw/edit)                                                                                                                                                                             |
|                             | FB AI@Scale [Making MLOps & DataOps a reality](https://www.facebook.com/atscaleevents/videos/ai-scale-flyte-making-mlops-and-dataops-a-reality/1047312585732459/)                                                                                                                      |
|                             | [GAIC 2020](http://www.globalbigdataconference.com/seattle/global-artificial-intelligence-virtual-conference-122/speaker-details/ketan-umare-113746.html)                                                                                                                              |

### Communication Channels

- [Slack Org](https://forms.gle/UVuek9WfBoweiqcJA)
- [Email list](https://groups.google.com/a/flyte.org/g/users)

### Biweekly Community Sync

- 📣 **Flyte OSS Community Sync** happens every alternate Tuesday, 9am-10am PDT ([Checkout the events calendar & subscribe](https://calendar.google.com/calendar/embed?src=admin%40flyte.org&ctz=America%2FLos_Angeles)). Here's the [zoom link](https://us04web.zoom.us/j/71298741279?pwd=TDR1RUppQmxGaDRFdzBOa2lHN1dsZz09).
- Meeting notes and backlog of topics are captured in [doc](https://docs.google.com/document/d/1Jb6eOPOzvTaHjtPEVy7OR2O5qK1MhEs3vv56DX2dacM/edit#heading=h.c5ha25xc546e).
- If you'd like to revisit any community sync meeting that has happened, you can access the [video recordings](https://www.youtube.com/channel/UCNduEoLOToNo3nFVly-vUTQ).

### Conference Talks

- Kubecon 2019 - Flyte: Cloud Native Machine Learning and Data Processing Platform [video](https://www.youtube.com/watch?v=KdUJGSP1h9U) | [deck](https://kccncna19.sched.com/event/UaYY/flyte-cloud-native-machine-learning-data-processing-platform-ketan-umare-haytham-abuelfutuh-lyft)
- Kubecon 2019 - Running LargeScale Stateful workloads on Kubernetes at Lyft [video](https://www.youtube.com/watch?v=ECeVQoble0g)
- re:invent 2019 - Implementing ML workflows with Kubernetes and Amazon Sagemaker [video](https://youtu.be/G-wzIQQJKaE)
- Cloud-native machine learning at Lyft with AWS Batch and Amazon EKS [video](https://youtu.be/n_rRb8u1GSM)
- OSS + ELC NA 2020 [splash](https://ossna2020.sched.com/event/313cec91aa38a430a25f9571039874b8)
- Datacouncil [splash](https://docs.google.com/document/d/1ZsCDOZ5ZJBPWzCNc45FhNtYQOxYHz0PAu9lrtDVnUpw/edit)
- FB AI@Scale [Making MLOps & DataOps a reality](https://www.facebook.com/atscaleevents/videos/ai-scale-flyte-making-mlops-and-dataops-a-reality/1047312585732459/)
- [GAIC 2020](http://www.globalbigdataconference.com/seattle/global-artificial-intelligence-virtual-conference-122/speaker-details/ketan-umare-113746.html)

### Blog Posts

1.  [Introducing Flyte: A Cloud Native Machine Learning and Data Processing Platform](https://eng.lyft.com/introducing-flyte-cloud-native-machine-learning-and-data-processing-platform-fb2bb3046a59)
2.  [Building a Gateway to Flyte](https://eng.lyft.com/building-a-gateway-to-flyte-474b451b32c8)

### Podcasts

- TWIML&AI - [Scalable and Maintainable ML Workflows at Lyft - Flyte](https://twimlai.com/twiml-talk-343-scalable-and-maintainable-workflows-at-lyft-with-flyte-w-haytham-abuelfutuh-and-ketan-umare/)
- Software Engineering Daily - [Flyte: Lyft Data Processing Platform](https://softwareengineeringdaily.com/2020/03/12/flyte-lyft-data-processing-platform-with-allyson-gale-and-ketan-umare/)
- MLOps Coffee session - [Flyte: an open-source tool for scalable, extensible, and portable workflows](https://anchor.fm/mlops/episodes/MLOps-Coffee-Sessions-12-Flyte-an-open-source-tool-for-scalable--extensible---and-portable-workflows-eksa5k)

## 💖 Top Contributors

A big thank you to the community for making Flyte possible!

- [@wild-endeavor](https://github.com/wild-endeavor)
- [@katrogan](https://github.com/katrogan)
- [@EngHabu](https://github.com/EngHabu)
- [@akhurana001](https://github.com/akhurana001)
- [@anandswaminathan](https://github.com/anandswaminathan)
- [@kanterov](https://github.com/kanterov)
- [@honnix](https://github.com/honnix)
- [@jeevb](https://github.com/jeevb)
- [@jonathanburns](https://github.com/jonathanburns)
- [@migueltol22](https://github.com/migueltol22)
- [@varshaparthay](https://github.com/varshaparthay)
- [@pingsutw](https://github.com/pingsutw)
- [@narape](https://github.com/narape)
- [@lu4nm3](https://github.com/lu4nm3)
- [@bnsblue](https://github.com/bnsblue)
- [@RubenBarragan](https://github.com/RubenBarragan)
- [@schottra](https://github.com/schottra)
- [@evalsocket](https://github.com/evalsocket)
- [@matthewphsmith](https://github.com/matthewphsmith)
- [@slai](https://github.com/slai)
- [@derwiki](https://github.com/derwiki)
- [@tnsetting](https://github.com/tnsetting)
- [@jbrambleDC](https://github.com/jbrambleDC)
- [@igorvalko](https://github.com/igorvalko)
- [@chanadian](https://github.com/chanadian)
- [@surindersinghp](https://github.com/surindersinghp)
- [@vsbus](https://github.com/vsbus)
- [@catalinii](https://github.com/catalinii)
- [@kumare3](https://github.com/kumare3)
