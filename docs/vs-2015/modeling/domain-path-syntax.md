---
title: Syntaxe cesty domény | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4b25b47b5b711f09334501ed21abf06cb66402b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669730"
---
# <a name="domain-path-syntax"></a>Syntaxe cesty domény
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definice DSL používají k vyhledání konkrétních prvků v modelu syntaxi typu XPath.

 Obvykle není nutné pracovat s touto syntaxí přímo. Kde se zobrazí v podrobnostech DSL nebo okno Vlastnosti, můžete kliknout na šipku dolů a použít Editor cest. Tato cesta se ale v tomto formuláři zobrazí v poli po použití editoru.

 Cesta k doméně má následující formát:

 *Vlastnost Relationship. PropertyName/! Role*

 ![Referenční vztah CommentReferencesSubjects](../modeling/media/dsl-reference.png "dsl_reference")

 Syntaxe projde stromovou strukturou modelu. Například doménový vztah **CommentReferencesSubjects** na ilustraci výše má roli **subjekty** . Segment cesty **/! Subject** – určuje, že cesta je dokončena na prvcích, které jsou k dispozici prostřednictvím role **subjekt** .

 Každý segment začíná názvem doménového vztahu. Pokud je průchod z prvku na relaci, segment cesty se zobrazí jako *Relationship. PropertyName*. Pokud je směrování z odkazu na element, segment cesty se zobrazí jako *vztah/! RoleName*.

 Lomítka oddělují syntaxi cesty. Každý segment cesty je buď směrování z prvku na odkaz (instance vztahu), nebo z odkazu na element. Segmenty cesty se často zobrazují ve dvojicích. Jeden segment cesty představuje směrování z prvku na odkaz a další segment představuje směrování z odkazu na element na druhém konci. (Jakékoli propojení může být také zdrojem nebo cílem samotného vztahu).

 Název, který použijete pro směrování elementu na propojení, je hodnotou role `Property Name` . Název, který použijete pro směrování propojení na prvky, je název cílové role.

## <a name="see-also"></a>Viz také
 [Porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md)
