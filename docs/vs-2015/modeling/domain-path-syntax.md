---
title: Syntaxe cesty domény | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain path
ms.assetid: 945994f9-72b9-42e0-81b2-e5fb3d0e282d
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d4e98715bae8869619e8d9f2852c810153984777
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49254771"
---
# <a name="domain-path-syntax"></a>Syntaxe cesty domény
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Definice DSL pomocí XPath syntaxe vyhledejte konkrétní prvky v modelu.  
  
 Obvykle není potřeba pracovat přímo s následující syntaxí. Kde se zobrazí v okně Vlastnosti, nebo podrobnosti DSL můžete klepnutím na šipku dolů a v editoru cestu. Cesta se však zobrazí v tomto formuláři v poli po použití editoru.  
  
 Doménová cesta má následující podobu:  
  
 *RelationshipName.PropertyName/! Role*  
  
 ![CommentReferencesSubjects – odkazová odkazovat na relaci](../modeling/media/dsl-reference.png "dsl_reference")  
  
 Syntaxe prochází stromu modelu. Například doménového vztahu **CommentReferencesSubjects – odkazová** na výše uvedeném obrázku má **Predmety** role. Segment cesty **/! Subjectt** Určuje, že cesta skončí u elementů přistupovat prostřednictvím **Predmety** role.  
  
 Spustí se každý segment s názvem doménového vztahu. Pokud procházení je z elementu relace, segment cesty se zobrazí jako *Relationship.PropertyName*. Pokud ke směrování je z odkazu na prvek, segment cesty se zobrazí jako *vztah /! RoleName*.  
  
 Lomítka samostatné syntaxe cesty. Každý segment cesty je směrování z elementu propojení (instance relace) nebo z odkazu na element. Segmenty cesty často vyskytovat v párech. Jeden segment cesty představuje hop z elementu propojení a další segment představuje hop z odkazu na prvek na druhém konci. (Odkaz může také být zdroj nebo cíl v relaci sama).  
  
 Název, který používáte pro prvek odkazu směrování je hodnota této role `Property Name`. Název, který používáte pro prvek odkazu směrování je cílový název role.  
  
## <a name="see-also"></a>Viz také  
 [Porozumění modelům, třídám a vztahům](../modeling/understanding-models-classes-and-relationships.md)



