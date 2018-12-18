---
title: 'CA2211: Nekonstantní pole by nemělo být viditelné | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 62c3ee28a3b7cbb9bef864483e254dda5f63bfae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894246"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: Nekonstantní pole by nemělo být viditelné
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|Kategorie|Microsoft.Usage|
|Narušující změna|Narušující|

## <a name="cause"></a>příčina
 Veřejný nebo chráněný statické pole není konstantní, ani není jen pro čtení.

## <a name="rule-description"></a>Popis pravidla
 Statická pole, která nejsou konstantami ani nejsou jen pro čtení, nejsou bezpečná pro přístup z více vláken. Přístup k takovému poli musí být pečlivě kontrolován a vyžaduje pokročilé programovací techniky pro synchronizaci přístupu k objektu třídy. Protože jde o obtížné dovednosti další a hlavní a testování takový objekt představuje vlastní výzvy, statická pole se nejlépe používají k ukládání dat, která se nezmění. Toto pravidlo platí pro knihovny; aplikace by neměly zveřejňovat žádná pole.

## <a name="how-to-fix-violations"></a>Jak vyřešit porušení
 Chcete-li opravit porušení tohoto pravidla, nastavit statické pole konstantní nebo jen pro čtení. Pokud to není možné změnit návrh typ, který má použít alternativní mechanismus například vlastnost bezpečné pro vlákna, která spravuje vlákno typově bezpečný přístup k podkladové pole. Uvědomte si, že problémy, jako je kolize zámků a zablokování může ovlivnit výkon a chování knihovny.

## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění
 Je bezpečné potlačit upozornění tohoto pravidla, pokud vyvíjíte aplikaci a proto mít plnou kontrolu nad přístup k typu, který obsahuje statické pole. Knihovna návrháře by neměl potlačit upozornění tohoto pravidla; použití statických polí, která není konstantní můžete provést s použitím knihovny obtížné pro vývojáře správně použít.

## <a name="example"></a>Příklad
 Následující příklad ukazuje typ, který porušuje tato pravidla.

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]



