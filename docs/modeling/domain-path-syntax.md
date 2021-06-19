---
title: Syntaxe cesty domény
description: Přečtěte si o syntaxi cesty k doméně a o tom, jak definice DSL používají syntaxi typu XPath k vyhledání konkrétních prvků v modelu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, domain path
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 69dfd02dca5ead65d4f36303e547aaeba04cde98
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389095"
---
# <a name="domain-path-syntax"></a>Syntaxe cesty domény
Definice DSL používají syntaxi typu XPath k vyhledání konkrétních prvků v modelu.

 S touto syntaxí obvykle pracovat přímo není. Tam, kde se zobrazuje v podrobnostech DSL nebo okno Vlastnosti, můžete kliknout na šipku dolů a použít editor cest. Cesta se ale zobrazí v tomto formuláři v poli po použití editoru.

 Cesta k doméně má následující podobu:

 *RelationshipName.PropertyName/! Roli*

 ![Referenční relace commentReferencesSubjects](../modeling/media/dsl_reference.png)

 Syntaxe prochádá strom modelu. Například relace domény **CommentReferencesSubjects** na obrázku výše má **roli Předměty.** Segment cesty **/! Předmět určuje,** že se cesta dokončí u prvků, ke kterým se přistupuje prostřednictvím role **Předměty.**

 Každý segment začíná názvem relace domény. Pokud procházení pochází z prvku do relace, zobrazí se segment cesty *jako Relationship.PropertyName*. Pokud segment směrování pochází z odkazu na prvek, zobrazí se segment cesty *Jako Relace/! Název role*.

 Lomítka odděluje syntaxi cesty. Každý segment cesty je buď segment směrování z prvku do propojení (instance relace), nebo z odkazu na prvek. Segmenty cest se často zobrazují v párech. Jeden segment cesty představuje segment směrování z prvku na odkaz a další segment představuje segment směrování z odkazu na prvek na druhém konci. (Libovolný odkaz může být také zdrojem nebo cílem samotné relace).)

 Název, který použijete pro segment směrování element-to-link, je hodnota role `Property Name` . Název, který použijete pro segment směrování link-to-element, je název cílové role.

## <a name="see-also"></a>Viz také

- [Porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md)
