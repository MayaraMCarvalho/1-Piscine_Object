# 🗂️ UML (Car Composition) - Module 02 - Piscine Object
(42 São Paulo)

Available in: [🇺🇸 English](README.en.md)

![Language](https://img.shields.io/badge/UML-model-blue.svg?logo=uml)
Este repositório contém a resolução do exercício 00 do Módulo 02 da Piscina de Objetos da 42 São Paulo. O objetivo é modelar a arquitetura de um sistema automotivo complexo utilizando a Linguagem de Modelagem Unificada (UML).

---

## 📜 Índice

* [Visão Geral do Projeto](#-vis%C3%A3o-geral-do-projeto)
* [Ferramentas Utilizadas](#%EF%B8%8F-ferramentas-utilizadas)
* [Estrutura do Diagrama](#-estrutura-do-diagrama)
* [Autora](#-autora)

---

## 🚗 Visão Geral do Projeto

O projeto consiste na criação de um **Diagrama de Classes** (`subject.png`) que representa a estrutura interna de um carro, incluindo motor, transmissão, direção, freios, eletrônica e controles de cockpit. O foco é demonstrar compreensão sólida de:

- Programação Orientada a Objetos (POO).
- Relacionamentos entre classes (Herança, Composição, Agregação).
- Padrões de Projeto (Singleton).
- Notação padrão UML.

> Entrega obrigatória: `ex00/subject.png` (PNG do diagrama de classes). Opcional: diagramas de sequência e documentação adicional.

---

## 🛠️ Ferramentas Utilizadas

- **Software de Diagramação:** StarUML
- **Formato de Entrega:** PNG

---

## 📋 Estrutura do Diagrama

O diagrama foi construído seguindo rigorosamente as especificações do *subject*, detalhando as seguintes estruturas:

### 1. Classes Abstratas e Interfaces
- **LinkablePart:** Atua como uma classe base virtual para componentes que podem receber comandos de pressão, como `Injector` e `BrakeController`.

### 2. O Núcleo do Carro (Composição)
A classe `Car` atua como o contêiner principal (Composição), agregando os subsistemas vitais:
- **Motor:** Composto internamente por `Injector`, `ExplosionChamber` e `Crankshaft`.
- **Transmission:** Gerencia a força enviada para as rodas.
- **Direction & BrakeController:** Sistemas de controle de movimento e frenagem.
- **Cockpit & Electronics:** Interfaces de usuário e controle eletrônico.

### 3. Padrões de Design
- **Singleton:** Aplicado na classe `GearLever` (Câmbio), garantindo que exista apenas uma instância de controle de marchas no sistema, herdando de `Singleton<GearLever>`.

### 4. Relacionamentos Chave
- **Composição (Diamante Preenchido):** Utilizada onde os objetos são instanciados diretamente dentro da classe (ex: `Motor` contém `Crankshaft`). Ou seja, onde a vida do componente depende do dono.
- **Agregação/Associação (Diamante Vazio):** Utilizada onde há referência via ponteiros (ex: `Transmission` aponta para `Wheel`). Ou seja, para coleções de objetos que podem existir independentemente.
- **Herança (Seta triangular):** Utilizada para especializações (ex: `Injector` **é um** `LinkablePart`).

---

## 💡 Decisões de Implementação e Bônus

Para garantir clareza e aderência às boas práticas de UML, as seguintes convenções foram adotadas no diagrama:

### 1. Multiplicidades
Foram definidas multiplicidades lógicas para o domínio automotivo:
* `Direction` ↔ `Wheel` : `2..*` (Mínimo de duas rodas direcionais).
* `Transmission` → `Wheel` : `0..*`.
* `Motor` (Composição): `1` para seus componentes internos vitais.

### 2. Visibilidade e Encapsulamento
* **Atributos:** Definidos como privados (`-`) para garantir o encapsulamento dos dados.
* **Métodos:** Definidos como públicos (`+`) quando representam a interface de comunicação do objeto (ex: `+ execute()`).

### 3. Diagramas de Sequência (Bônus)
Foram elaborados diagramas adicionais para ilustrar a interação entre objetos em cenários críticos:
1. **Aceleração:** Fluxo de `Pedal` até `Wheel`.
2. **Frenagem:** Atuação do `BrakeController`.

---

# 👩🏻 Autora
**Mayara Carvalho**
<br>
[:octocat: @MayaraMCarvalho](https://github.com/MayaraMCarvalho) | 42 Login: `macarval`

---
