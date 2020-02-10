---
reviewers:
- bgrant0607
- mikedanese
title: Що ж таке Kubernetes?
content_template: templates/concept
weight: 10
card:
  name: concepts
  weight: 10
---

{{% capture overview %}}
<!--
This page is an overview of Kubernetes.
-->
Ця сторінка являє собою узагальнений огляд Kubernetes.
{{% /capture %}}

{{% capture body %}}
<!--
Kubernetes is a portable, extensible, open-source platform for managing containerized workloads and services, that facilitates both declarative configuration and automation. It has a large, rapidly growing ecosystem. Kubernetes services, support, and tools are widely available.
-->
Kubernetes - це платформа з відкритим джерельним кодом для управління контейнеризованими робочим навантаженнями та супутніми службами. Її основні властивості - кросплатформенність, розширюваність, успішне використання декларативної конфігурації та автоматизації. Вона має гігантську, швидкопрогресуючу екосистему.

<!--
The name Kubernetes originates from Greek, meaning helmsman or pilot. Google open-sourced the Kubernetes project in 2014. Kubernetes builds upon a [decade and a half of experience that Google has with running production workloads at scale](https://ai.google/research/pubs/pub43438), combined with best-of-breed ideas and practices from the community.
-->
Назва Kubernetes походить з грецької та означає керманич, або пілот. Google відкрив доступ до джерельних кодів проекту Kubernetes у 2014 році. Kubernetes побудовано [на базі п'ятнадцятилітнього досвіду, що Google отримав, оперуючи масштабними робочим навантаженнями](https://ai.google/research/pubs/pub43438) у купі з найкращими у своєму класі ідеями та практиками, які може запропонувати спільнота.

<!--
## Going back in time
-->
## Подорожуючи назад у часі.

<!--
Let's take a look at why Kubernetes is so useful by going back in time.
-->
Давайте повернемось назад у часі та дізнаємось, завдяки чому Kubernetes став таким корисним.

![Deployment evolution](/images/docs/Container_Evolution.svg)

<!--
*Traditional deployment era:** Early on, organizations ran applications on physical servers. There was no way to define resource boundaries for applications in a physical server, and this caused resource allocation issues. For example, if multiple applications run on a physical server, there can be instances where one application would take up most of the resources, and as a result, the other applications would underperform. A solution for this would be to run each application on a different physical server. But this did not scale as resources were underutilized, and it was expensive for organizations to maintain many physical servers.
-->
**Ера традиційного розгортання:** На початку, організації запускали застосунки на фізичних серверах. Не існує способу задати обмеження використання ресурсів у такий спосіб, що спричиняло проблему виділення та розподілення ресурсів на фізичних серверах. Наприклад: якщо багато застосунків було запущено на фізичному сервері, могли траплятись випадки коли один застосунок забирав собі найбільше ресурсів, і як результат, інші програми просто недопрацьовували. Рішенням для цього було б запускати кожний застосунок  на окремому фізичному сервері. Але таке рішення погано масштабувалось, оскільки ресурси була не повністю використані; на додачу таке рішення коштувало дорого тому що організаціям потрібно було опікуватись фізичними серверами.

<!--
**Virtualized deployment era:**  As a solution, virtualization was introduced. It allows you to run multiple Virtual Machines (VMs) on a single physical server's CPU. Virtualization allows applications to be isolated between VMs and provides a level of security as the information of one application cannot be freely accessed by another application.
-->
**Ера віртуалізованого розгортання:** Як рішення - була представлена віртуалізвація. Вона дозволяла запускати багаточисленні Віртуальні Машини (Virtual Machines або VMs) на одному фізичному серверному ЦПУ. ВІртуалізвація дозволила застосункам бути ізольованими у межах Віртуальних Машин та забезпечувала безпеку оскільки інформація застосунку на одній VM не була доступна застосунку на іншій VM.
<!--
Virtualization allows better utilization of resources in a physical server and allows better scalability because an application can be added or updated easily, reduces hardware costs, and much more. With virtualization you can present a set of physical resources as a cluster of disposable virtual machines.
-->
Віртуалізація дозволяла кращу утилізацію ресурсів на фізичному сервері на додачу до кращої масштабованості, тому що застосунок міг бути доданий або оновлений набагато легше, що зменшувало вартість на доадачу до іншого. З віртуалізцацією ви могли представити ресурси у вигляді одноразових віртуальних машин.

<!--
Each VM is a full machine running all the components, including its own operating system, on top of the virtualized hardware.
-->
Кожна VM являє собою повноцінну машину з усіма компонентами, включаючи операційну систему, поверх віртуалізаційного апаратного забезпечення.

<!--
**Container deployment era:** Containers are similar to VMs, but they have relaxed isolation properties to share the Operating System (OS) among the applications. Therefore, containers are considered lightweight. Similar to a VM, a container has its own filesystem, CPU, memory, process space, and more. As they are decoupled from the underlying infrastructure, they are portable across clouds and OS distributions.
-->
**Ера розгортання контейнерів:** Контейнери схожі на VM, але мають спрощені характеристики ізольованості і розділяють операційну систему з усіма застосунками. Саму тому контейнери вважались легковісними. Подібно по VM, контейнер мав власну файлову систему, ЦПУ, пам'ять, простір процесів, тощо. Так як вони вивільнені від підпорядкованої інфраструктури, контейнери можуть вільно пересуватись між хмарними провайдерами або дистрибутивами операційних систем.
<!--
Containers have become popular because they provide extra benefits, such as:
-->
Контейнери стали популярнішими тому що пропонували додаткові переваги, такі як:

<!--
* Agile application creation and deployment: increased ease and efficiency of container image creation compared to VM image use.
* Continuous development, integration, and deployment: provides for reliable and frequent container image build and deployment with quick and easy rollbacks (due to image immutability).
* Dev and Ops separation of concerns: create application container images at build/release time rather than deployment time, thereby decoupling applications from infrastructure.
* Observability not only surfaces OS-level information and metrics, but also application health and other signals.
* Environmental consistency across development, testing, and production: Runs the same on a laptop as it does in the cloud.
* Cloud and OS distribution portability: Runs on Ubuntu, RHEL, CoreOS, on-prem, Google Kubernetes Engine, and anywhere else.
* Application-centric management: Raises the level of abstraction from running an OS on virtual hardware to running an application on an OS using logical resources.
* Loosely coupled, distributed, elastic, liberated micro-services: applications are broken into smaller, independent pieces and can be deployed and managed dynamically – not a monolithic stack running on one big single-purpose machine.
* Resource isolation: predictable application performance.
* Resource utilization: high efficiency and density.
-->

* Створення та розгортання застосунків за методологією Agile: збільшення простоти та ефективності створення образів контейнерів у порівнянні до використання образів віртуальних машин.
* Безперервна розробка, інтеграція та розгортання: забезпечення надійних та безперервних побудов контейнерів та їх швидке розгортання та легкі відкатування (за рахунок незмінності образів).
* Розподіл сумнівів розробки та операцій: створення образів контейнерів застосунків під час побудови/релізу на противагу часу розгортання, і як наслідок, вивільнення застосунків із інфраструктури.
* Спостереження не тільки за інформацією та метриками рівня операційної системи, а такою станом застосунку та іншими сигналами.
* Однорідність середовища для розробників, тестів та робочого навантаження: запускаємо те саме на вашому робочому комп'ютері, що і у хмарного провайдера.
* Хмарна та Операційно-Системна переносимість: запускається на  Ubuntu, RHEL, CoreOS, у власному дата центрі, Google Kubernetes Engine, і взагалі будь де.
* Application-centric management: Raises the level of abstraction from running an OS on virtual hardware to running an application on an OS using logical resources.
* Застосунко-центроване керування: підвищення рівня абстрації від запуску операційної системи у віртуальному апаратному забезпеченні до запуску застосунка в операціні системі використовуючи логічні ресурси.
* Нещільно поєднані, розподілені, еластичні, звільнені мікро-сервіси: застосунки розбиваються у менші, незалежні частини що можуть бути розгорнутими та скерованими динамічно - не як монолітна побудова що працює на одній великій машині, що і є її єдиною ціллю.
* Ізоляція ресурсів: передбачувана якість роботи застосунків.
* Використання ресурсів: висока ефективність та щільність.

<!--
## Why you need Kubernetes and what can it do
-->
## Чому вам потрібен Kebernetes та що він може робити

<!--
Containers are a good way to bundle and run your applications. In a production environment, you need to manage the containers that run the applications and ensure that there is no downtime. For example, if a container goes down, another container needs to start. Wouldn't it be easier if this behavior was handled by a system?
-->
Контейнери прекрасний спосіб створення та запуску ваших застосунків. В робочому оточенні, вам потрібно керувати контейнерами (в яких працюють застосунки) та впевнюватись що не буде жодного простою. Наприклад, якщо один контейнер припиняє роботу, інших повинен бути запущеним йому на заміну. Було б непогано щоб системи керувала такими випадками?

<!--
That's how Kubernetes comes to the rescue! Kubernetes provides you with a framework to run distributed systems resiliently. It takes care of scaling and failover for your application, provides deployment patterns, and more. For example, Kubernetes can easily manage a canary deployment for your system.
-->
Ось тут то Kuberntes приходе на допомогу! Kubernetes надає нам основу робочих інструментів для запуску еластичних розподілених систем. Він бере на себе обов'язки опіки за масштабуванням та аварійним відновленням вашого застосунку, пропонуує шаблони розгортань, тощо. Наприклад, Kubernetes дозволяє легко створювати канаркові розгортання у вашій системі.

<!--
Kubernetes provides you with:
-->
Kubernetes надає вам:

<!--
* **Service discovery and load balancing**
Kubernetes can expose a container using the DNS name or using their own IP address. If traffic to a container is high, Kubernetes is able to load balance and distribute the network traffic so that the deployment is stable.
* **Storage orchestration**
Kubernetes allows you to automatically mount a storage system of your choice, such as local storages, public cloud providers, and more.
* **Automated rollouts and rollbacks**
You can describe the desired state for your deployed containers using Kubernetes, and it can change the actual state to the desired state at a controlled rate. For example, you can automate Kubernetes to create new containers for your deployment, remove existing containers and adopt all their resources to the new container.
* **Automatic bin packing**
You provide Kubernetes with a cluster of nodes that it can use to run containerized tasks. You tell Kubernetes how much CPU and memory (RAM) each container needs. Kubernetes can fit containers onto your nodes to make the best use of your resources.
* **Self-healing**
Kubernetes restarts containers that fail, replaces containers, kills containers that don’t respond to your user-defined health check, and doesn’t advertise them to clients until they are ready to serve.
* **Secret and configuration management**
Kubernetes lets you store and manage sensitive information, such as passwords, OAuth tokens, and SSH keys. You can deploy and update secrets and application configuration without rebuilding your container images, and without exposing secrets in your stack configuration.
-->

* **Визначення сервісів та балансування навантаження**
Kubernetes може надавати доступ до контейнера використовуючи DNS ім'я або його власну IP адресу. Якщо мережеве навантаження до контейнера завелике, Kubernetes здатний збалансувати та розподілити його так щоб розгортання залишалось стабільним.
* **Оркестрація сховища інформації**
Kubernetes дозволяє вам автоматично монтувати системи збереження інформації на ваш вибір: локальні сховища, пропозиції хмарних провайдерів, тощо.
* **Автоматичні оновлення та відкатування**
Використовуючи Kubernetes ви можете описати бажаний стан контейнерів що розгортаються, і він прослідкує за досягненням цього стану в контрольованій манері. Наприклад, ви можете автоматизувати Kubernetes створювати нові контейнери для вашого розгортання, згортати старі та передавати їхні ресурси на новостворені контейнери.
* **Автоматичне розміщення завдань**
Ви задовольняєте потребу Kubernetes у кластері робочих машин (нод), що будуть використані для запуску контейнерних завдань, і вказавши скільки ЦПУ та пам'яті необхідно кожному контейнеру Kuberentes розподілить контейнери по нодам так що використання ресурсів буде оптимальним.
* **Самозцілення**
Kubernetes перезавантажить контейнер що дає збої, замінить контейнери, припинить роботу таких що не відповідають на визначені користувачем перевірки стану, і не буде оголошувати їх наявність системі допоки вони не будуть готові до обслуговування.
* **Управління секретами та конфігурацією**
Kubernetes дозволяє вам зберігати та керувати чутливою інформацією, такою як: паролі, OAuth токени та SSH ключі. Ви можете публікувати або оновлювати секрети та конфігурацю без перебудови образів ваших контейнерів, та без публікації цієї інформації до усієї системи.

<!--
## What Kubernetes is not
-->

## Чим Kubernetes не є

<!--
Kubernetes is not a traditional, all-inclusive PaaS (Platform as a Service) system. Since Kubernetes operates at the container level rather than at the hardware level, it provides some generally applicable features common to PaaS offerings, such as deployment, scaling, load balancing, logging, and monitoring. However, Kubernetes is not monolithic, and these default solutions are optional and pluggable. Kubernetes provides the building blocks for building developer platforms, but preserves user choice and flexibility where it is important.
-->
Kubernetes не є традиційною, системою PaaS все-включено (Платформа як послуга). Kubernetes оперує скорше на рівні контейнерів, ніж на рівні апаратного забезпечення, деякі особливості платформи якими вона пропонує є спільними і для PaaS пропозицій - це розгортання, масштабування, розподіл навантаження, протоколювання і спостереження. Незважаючи на це, Kubernetes не є монолітним, і вищезазначені особливості є опціональними і такими, що можуть бути вимкнутими. Kubernetes надає інструменти та матеріали для створення платформ дял розробки, але залишає за користувачем право вибору у важливих питаннях.

Kubernetes:

<!--
* Does not limit the types of applications supported. Kubernetes aims to support an extremely diverse variety of workloads, including stateless, stateful, and data-processing workloads. If an application can run in a container, it should run great on Kubernetes.
* Does not deploy source code and does not build your application. Continuous Integration, Delivery, and Deployment (CI/CD) workflows are determined by organization cultures and preferences as well as technical requirements.
* Does not provide application-level services, such as middleware (for example, message buses), data-processing frameworks (for example, Spark), databases (for example, MySQL), caches, nor cluster storage systems (for example, Ceph) as built-in services. Such components can run on Kubernetes, and/or can be accessed by applications running on Kubernetes through portable mechanisms, such as the [Open Service Broker](https://openservicebrokerapi.org/).
* Does not dictate logging, monitoring, or alerting solutions. It provides some integrations as proof of concept, and mechanisms to collect and export metrics.
* Does not provide nor mandate a configuration language/system (for example, Jsonnet). It provides a declarative API that may be targeted by arbitrary forms of declarative specifications.
* Does not provide nor adopt any comprehensive machine configuration, maintenance, management, or self-healing systems.
* Additionally, Kubernetes is not a mere orchestration system. In fact, it eliminates the need for orchestration. The technical definition of orchestration is execution of a defined workflow: first do A, then B, then C. In contrast, Kubernetes comprises a set of independent, composable control processes that continuously drive the current state towards the provided desired state. It shouldn’t matter how you get from A to C. Centralized control is also not required. This results in a system that is easier to use and more powerful, robust, resilient, and extensible.
-->

* Не обмежує типи застосунків що підтримуються. Kuberntes намагається підтримувати екстримально різноманітні типи навантажень, включаючи такі яким потрібне зберігання стану так і такі яким воно непотрібне, навантаження по обробці даних, тощо. Якщо застосунок може бути запущений в контейнері - він має відчувати себе добре у Kubernetes.
* Не розгортає застосунки з джерельних кодів та не будує ваші застосунки. Процеси безперервної інтеграції, доставка та розгортання (так звані CI/CD інструменти) визначаються на рівні організації, та потребами технічних вимог.
* Не надає сервіси на рівні застосунків як вбудовані: програмне забезпечення проміжного рівня (наприклад, шина передачі повідомлень), фреймворки обробки даних (наприклад, Spark), бази даних (наприклад, MySQL), кеш, некластерні системи збереження інформації (наприклад, Ceph). Ці компоненти можуть бути запущені у Kubernetes та/або бути доступними для застосунків за допомогою спеціальних механізмів, наприклад [Open Service Broker](https://openservicebrokerapi.org/).
* Не змушує використовувати рішення для протоколювання, моніторингу та сповіщень, натомість дозволяє використовувати деякі інтеграції як доказ що це можливо, та механізми по збору та експорту метрик.
* Не надає та не змушує використовувати якусь конфігураційну мову/систему (як наприклад `Jsonnet`), натомість надає можливість використовувати API що може бути використаний довільними формами декларативних специфікацій.
* Не надає і не планує вбудовувати будь-яку систему машинної конфігурації, обслуговування, управління або самозцілення.
* На додачу, Kubernetes не просто система оркестрації. Насправді, вона прибирає потребу оркестрації як такої. Технічне визначення оркестрації - це запуск визначених процесів: спочатку A, за ним B, потім C. На противагу, - Kubernetes складається з певної множити незалежних, складних процесів контролерів, що безперервно опрацьовують стан у напрямку заданого бажаною конфігурацією. Не має бути важливим як ви дістанетесь з пункту A до пункту C. Централізоване управління також не є вимогою. Це все виливається в систему яку легко використовувати, яка є потужною, надійною, стійкою та здатною до легкого розширення.

{{% /capture %}}

{{% capture whatsnext %}}
<!--
*   Take a look at the [Kubernetes Components](/docs/concepts/overview/components/)
*   Ready to [Get Started](/docs/setup/)?
-->
*   Зверніть увагу на [компоненти Kubernetes](/docs/concepts/overview/components/)
*   Готові [розпочати роботу](/docs/setup/)?
{{% /capture %}}
