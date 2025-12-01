# 🗂️ UML (Car Composition) - Module 02 - Piscine Object
(42 São Paulo)

Available in: [🇺🇸 English](README.en.md)

![Language](https://img.shields.io/badge/UML-model-blue.svg?logo=uml)
Este repositório contém a resolução do exercício 00 do Módulo 02 da Piscina de Objetos da 42 São Paulo. O objetivo é modelar a arquitetura de um sistema automotivo complexo utilizando a Linguagem de Modelagem Unificada (UML).

---

## 📜 Índice

* [Visão Geral do Projeto](https://github.com/MayaraMCarvalho/1-Piscine_Object/tree/master/Module_02-UML/ex00#-vis%C3%A3o-geral-do-projeto)
* [Ferramentas Utilizadas](https://github.com/MayaraMCarvalho/1-Piscine_Object/tree/master/Module_02-UML/ex00#%EF%B8%8F-ferramentas-utilizadas)
* [Estrutura do Diagrama](https://github.com/MayaraMCarvalho/1-Piscine_Object/tree/master/Module_02-UML/ex00#-estrutura-do-diagrama)
* [Autora](https://github.com/MayaraMCarvalho/1-Piscine_Object/tree/master/Module_02-UML#-autora)

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
- **Agregação/Associação (Diamante Vazio ou Seta):** Utilizada onde há referência via ponteiros (ex: `Transmission` aponta para `Wheel`). Ou seja, para coleções de objetos que podem existir independentemente.
- **Herança (Seta triangular):** Utilizada para especializações (ex: `Injector` **é um** `LinkablePart`).

### 5. Multiplicidades sugeridas (exemplos práticos)

* `Direction` → `Wheel` : `2..*` (duas ou mais rodas vinculadas à direção)
* `Transmission` → `Wheel` : `0..*` (transmissão pode não ter wheels conectadas em modelos isolados)
* `Motor` contém `Injector`, `ExplosionChamber`, `Crankshaft` : `1` (composição)
* `Car` contém `BrakeController`, `Direction`, `Transmission`, `Motor`, `Electronics`, `Cockpit` : `1`

> Ajuste multiplicidades se você tiver motivos específicos (ex.: veículo com 4 rodas exatas: use `4`).

### 6. Visibilidade e nomes (convenções)

* Atributos privados: prefixo `-` (ex.: `- demultiplier: int`).
* Métodos públicos: prefixo `+` (ex.: `+ void execute(float p_pression)`).
* Métodos/propriedades protegidos: `#` quando necessário.

Sugestão: mantenha atributos privados e forneça getters/setters públicos apenas quando necessário para a lógica de domínio.

### 7. Diagramas de sequência (bônus) — cenários sugeridos

1. **Acelerar** (Pedal → Injector → ExplosionChamber → Crankshaft → Transmission → Wheel)
2. **Frear** (Pedal/Freio → BrakeController → Brake → Wheel)
3. **Girar** (SteerWheel → DAE → Direction → Wheel)

Crie arquivos `sequence_accelerate.puml`, etc., e gere PNGs com PlantUML ou exporte do draw.io.

---

# 👩🏻 Autora
[Mayara Carvalho / macarval]

---
