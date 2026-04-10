---
title: Work
subtitle:
comments: false
---

| Projects                                    | Tools & Technologies                                                    |
|---------------------------------------------|-------------------------------------------------------------------------|
| [Payment Plan Advisor](#payment-plan-advisor)       | JavaScript, React, Node.js, AWS, Amazon Bedrock                         |
| [OptiCharge](#opticharge)                   | Go, JavaScript, React, Node.js, AWS                                     |
| [Bequest](#bequest)                         | Go, JavaScript, React, Node.js, Docker, Kubernetes, AWS, Event Sourcing |
| [ChatGPT Discord Bot](#chatgpt-discord-bot) | Go, ChatGPT, Instant Messaging, Bot                                     |
| [Cool X Wallet](#cool-x-wallet)             | JavaScript, React Native, AWS Cloud HSM, Docker, Blockchain             |
| [CoolWallet S](#coolwallet-s)               | Go, Blockchain, CI/CD, JavaScript, React Native                         |
| [Spark API](#spark-api)                     | REST API, Blockchain                                                    |
| [Sygna Bridge](#sygna-bridge)               | React, Redux, Saga, JavaScript, AWS Fargate, NodeJS                     |
| [Resumake](#resumake)                       | React, JavaScript, Node.js                                              |

---
### Payment Plan Advisor

An AI-powered chatbot built for customers facing financial difficulty. The chatbot assesses each customer's individual circumstances and proposes a tailored, realistic payment plan to help them manage debt — combining conversational AI with human specialist oversight to ensure fairness, compliance, and support for vulnerable customers.

- Served as **Technical Lead** across a cross-functional team of 5 engineers, 2 product owners, and a solution architect — driving technical direction from high-level architecture down to implementation details.
- Owned end-to-end **DevOps**: designed and managed CI/CD pipelines, infrastructure-as-code, and cloud deployment on AWS, ensuring reliable and repeatable delivery.
- Architected an **event-driven microservices system** underpinning the chatbot, orchestrating services via asynchronous events to decouple components, improve resilience, and support independent scaling — with **Amazon Bedrock Agents** coordinating multi-step reasoning and tool use to assess customer circumstances and generate personalised payment plans.
- Built **Full Conversation Visibility** for the payment team, surfacing complete chat history to reduce time-to-context and enable faster, better-informed specialist decisions.
- Engineered a **self-serve provisional payment plan** flow allowing customers to draft their own plans, which are then reviewed and approved by a specialist before going live.
- Integrated **assisted account actions** — in-flow payment submission and meter reading capture — directly within the chat experience, removing the need for customers to switch channels.

![](/img/payment-plan-advisor.gif)

### OptiCharge

Migrated eligible customers to a new tariff offering reduced electric vehicle charging rates during off-peak hours.

- Led the **micro frontend architecture** in React, integrating modular UIs into a legacy monolith to modernise the platform and reduce cross-team deployment coupling.
- Designed and built a **Go-based GraphQL simulation tool** to mock and validate APIs with authentic data, cutting backend dependencies and accelerating the development lifecycle by 10%.

![](/img/ev.gif)

### Bequest

Personalised pay-as-you-go life insurance and online wills.

- Integrated the **Stripe payment gateway** using Go, adding a new monetisation channel that increased revenue by 10%.
- Architected a **multi-tenant white-labelling system** using Go, Docker, and AWS EKS, enabling the business to offer customised solutions to clients and attract new business.
- Automated the **database migration process** in Go, reducing time spent on manual migration tasks and increasing development speed by 10%.
- Improved **web performance by 20%** by refactoring the API consumption module in React and Go, measured by enhanced response times.
- Enhanced the **event-driven microservices architecture** using Go, improving platform throughput, resilience, and scalability across services.
- Built **dynamic React environment variable injection**, enabling the app to deploy across multiple environments without code changes.

![](/img/bequest.png)

---

### ChatGPT Discord Bot

A Discord bot enabling real-time AI-powered natural language conversations using OpenAI's ChatGPT model.

_[View Project](https://github.com/rayspock/go-chatgpt-discord)_

- Built a **ChatGPT-powered Discord bot** in Go integrating the OpenAI API, enabling real-time conversational interactions to automate and enhance user engagement directly within Discord servers.

![](https://user-images.githubusercontent.com/19812545/239699730-28bc4608-871f-4477-bbb4-fcfbbdbe9a27.gif)

### Cool X Wallet

Credit card-sized Bluetooth hardware wallet to secure customers' crypto assets.

- Engineered **AWS Cloud HSM infrastructure** at [SBI](https://www.crunchbase.com/organization/sbi-bits), providing enterprise-grade secure key storage and cryptographic operations underpinning the hardware wallet.

![](/img/coolx.jpg)

---

### CoolWallet S

Bluetooth hardware wallet for Bitcoin, Ethereum, Litecoin, XRP, Bitcoin Cash, and ERC20 Tokens — storing users' private keys in a secure offline hardware device.

_[View Project](https://www.coolwallet.io/)_

- Implemented **top-level security measures** in JavaScript to protect crypto assets, contributing to over 100,000 wallet sales worldwide.
- Established a **CI/CD pipeline** to automate build and release workflows, improving delivery speed and reducing manual deployment errors.
- Built and maintained the **React Native mobile application**, delivering a consistent cross-platform wallet management experience across iOS and Android.

![](/img/coolwallet.jpg)

---

### Spark API

> Forked from [kyuupichan/electrumx](https://github.com/kyuupichan/electrumx)

Exposes blockchain data via REST, enabling developers to interact with the blockchain programmatically.

_[View Project](https://github.com/rayspock/electrumx)_

- Built **REST APIs** on ElectrumX to expose blockchain data and interactions, improving node sync performance by 20%.

![](/img/blockchain.jpg)

---

### Sygna Bridge

Compliance infrastructure bridging the virtual asset industry and mainstream finance, enabling VASPs to collect and exchange regulation-required transaction information.

_[View Project](https://www.sygna.io/bridge/)_

- Designed and established the **AWS Serverless and Fargate infrastructure** for Sygna, delivering highly scalable and maintainable REST APIs.
- Developed **compliance web applications** using JavaScript and asynchronous message queues, increasing user engagement by 15%.

![](/img/bridge.jpg)

---

### Resumake

Resumake automatically generates elegant LaTeX resumes without requiring users to write any TeX code themselves.

_[View Project](https://resumake.io/)_

- Contributed a new **resume template** as an open-source addition, giving users a polished layout option that streamlines the process of creating a professional standout resume.

![](/img/resumake.jpg)
