---
title: Sada Modeling SDK pro sadu Visual Studio – jazyky domény
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2abb209943ff14969f71ebdca6982020f30a5d47
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590199"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Sada Modeling SDK pro sadu Visual Studio – jazyky domény

Pomocí sady SDK modelování pro sadu Visual Studio můžete vytvořit výkonné založené na modelu vývojářské nástroje, které můžete integrovat do sady Visual Studio. Stejným způsobem můžete vytvořit jednu nebo několik definic modelu a integrovat je do sady nástrojů.

V centru MSDK je definice modelu, který je vytvořen, aby představoval pojmy v oblasti vašeho podnikání. Je možné ohraničit model s celou řadu nástrojů, jako je diagramatické zobrazení, možnost generování kódu a další artefakty, příkazů pro transformaci modelu a možnost interakce s kódem a dalšími objekty v sadě Visual Studio. Při vývoji lze model kombinovat s dalšími modely a nástroji, jež tvoří výkonnou sadu nástrojů, které jsou zaměřeny na vývoj.

MSDK umožňuje rychlý vývoj modelu ve formě jazyka specifického pro doménu (DSL). Začínáte se speciálním editorem, kterým definujete schéma nebo abstraktní syntaxi a grafickou notaci. Z této definice vygeneruje VMSDK následující položky:

- Model implementace s rozhraním API silného typu, který je spuštěn v obchodě založeném na transakcích.

- Průzkumník založený na stromové architektuře.

- Grafický editor, ve kterém uživatelé mohou zobrazit model nebo jeho části, které definujete.

- Metody serializace, které uloží modely ve formátu XML pro čtení.

- Zařízení pro generování programového kódu a jiných artefaktů pomocí šablonování textu.

Můžete přizpůsobit a rozšířit všechny tyto funkce. Vaše rozšíření jsou integrována tak, že můžete i nadále aktualizovat definici DSL a znovu generovat funkce bez ztráty rozšíření.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[Související blogové příspěvky](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
