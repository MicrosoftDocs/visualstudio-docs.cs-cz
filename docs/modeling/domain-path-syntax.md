---
title: Syntaxe cesty domény
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d7ab5f080328338e40bed080ec8a4c7a85eabdb
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114635"
---
# <a name="domain-path-syntax"></a>Syntaxe cesty domény
Definice DSL používají k vyhledání konkrétních prvků v modelu syntaxi typu XPath.

 Obvykle není nutné pracovat s touto syntaxí přímo. Kde se zobrazí v podrobnostech DSL nebo okno Vlastnosti, můžete kliknout na šipku dolů a použít Editor cest. Tato cesta se ale v tomto formuláři zobrazí v poli po použití editoru.

 Cesta k doméně má následující formát:

 *Vlastnost Relationship. PropertyName/! Role*

 ![Referenční vztah CommentReferencesSubjects](../modeling/media/dsl_reference.png)

 Syntaxe projde stromovou strukturou modelu. Například doménový vztah **CommentReferencesSubjects** na ilustraci výše má roli **subjekty** . Segment cesty **/! Subject** – určuje, že cesta je dokončena na prvcích, které jsou k dispozici prostřednictvím role **subjekt** .

 Každý segment začíná názvem doménového vztahu. Pokud je průchod z prvku na relaci, segment cesty se zobrazí jako *Relationship. PropertyName*. Pokud je směrování z odkazu na element, segment cesty se zobrazí jako *vztah/! RoleName*.

 Lomítka oddělují syntaxi cesty. Každý segment cesty je buď směrování z prvku na odkaz (instance vztahu), nebo z odkazu na element. Segmenty cesty se často zobrazují ve dvojicích. Jeden segment cesty představuje směrování z prvku na odkaz a další segment představuje směrování z odkazu na element na druhém konci. (Jakékoli propojení může být také zdrojem nebo cílem samotného vztahu).

 Název, který použijete pro směrování elementu na propojení, je hodnota `Property Name`role. Název, který použijete pro směrování propojení na prvky, je název cílové role.

## <a name="see-also"></a>Viz také:

- [Porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md)
