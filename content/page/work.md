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
## Payment Plan Advisor

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

- Led the architecture and implementation of micro frontends in React, successfully integrating them into an existing monolithic application. This modernised the platform, improved scalability and maintainability, and enhanced the customer experience. 
- Designed and built a Go-based simulation tool to mock and validate GraphQL APIs, extending the legacy API with authentic data. This reduced backend dependencies, accelerated the development lifecycle by 10%, and improved application reliability and resilience.

![](/img/ev.gif)

### Bequest

Personalised pay-as-you-go life insurance and online wills.
I mainly focused on building the backend and leveraging microservices architectures to achieve the Performance,
Reliability, Availability and Scalability (PRAS).

![](/img/bequest.png)

---

### ChatGPT Discord Bot

The GPT Discord Bot project, which is developing a bot using OpenAI's ChatGPT model to enhance and automate interactions
on the popular Discord messaging platform, combining the power of AI technology with the social aspect of a chat
platform to create unique and engaging experiences for users.

![](https://user-images.githubusercontent.com/19812545/239699730-28bc4608-871f-4477-bbb4-fcfbbdbe9a27.gif)

### Cool X Wallet

Credit Card-Sized Bluetooth hardware wallet to secure customer's crypto assets.
I built Hardware Security Module (HSM) infrastructure for Cool X Wallet in [SBI](https://www.crunchbase.com/organization/sbi-bits).

![](/img/coolx.jpg)

---

### CoolWallet S

Bluetooth hardware wallet for Bitcoin, Ethereum, Litecoin, XRP, Bitcoin Cash, and ERC20 Tokens.

A hardware wallet is a special type of bitcoin wallet which stores the user's private keys in a secure hardware device.

_[View Project](https://www.coolwallet.io/)_

![](/img/coolwallet.jpg)

---

### Spark API

> Forked from [kyuupichan/electrumx](https://github.com/kyuupichan/electrumx)

Built REST APIs on ElectrumX for people to interact with the blockchain and increase syncing performance by 20%.

_[View Project](https://github.com/rayspock/electrumx)_

![](/img/blockchain.jpg)

---

### Sygna Bridge

Sygna Bridges the Gap Between the Virtual Asset Industry and Mainstream Finance. Visually exploring Sygna Bridge which
enabling VASPs to collect and exchange compliance-required transaction information.

_[View Project](https://www.sygna.io/bridge/)_

![](/img/bridge.jpg)

---

### Resumake

Resumake is a website for automatically generating elegant LaTeX resumes without the need to write any TeX code
yourself.

As an open-source contributor, I provided a solution by developing a new template to choose from, which enable users to
highlight their resumes.

_[View Project](https://resumake.io/)_

![](/img/resumake.jpg)
