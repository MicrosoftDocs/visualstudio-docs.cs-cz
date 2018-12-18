---
title: 'CA1500: Názvy proměnných by neměly odpovídat názvům polí | Dokumentace Microsoftu'
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
- VariableNamesShouldNotMatchFieldNames
- CA1500
helpviewer_keywords:
- VariableNamesShouldNotMatchFieldNames
- CA1500
ms.assetid: fa0e5029-79e9-4a33-8576-787ac3c26c39
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: fdac60aa7b3fb37f45cff7c1c9e5f17920efed18
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49173937"
---
# <a name="ca1500-variable-names-should-not-match-field-names"></a>CA1500: Názvy proměnných by neměly odpovídat názvům polí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio 2017, najdete v části [CA1500: názvy proměnných by neměly odpovídat názvům polí](https://docs.microsoft.com/visualstudio/code-quality/ca1500-variable-names-should-not-match-field-names) na webu docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|VariableNamesShouldNotMatchFieldNames|  
|CheckId|CA1500|  
|Kategorie|Microsoft.Maintainability|  
|Narušující změna|Při vyvolání na parametr, který má stejný název jako pole:<br /><br /> – Pevná – Pokud pole a metody, která deklaruje parametr je nemohou vidět mimo sestavení, bez ohledu na to, které provedete změnu.<br />-Zásadní - li změnit název pole a jsou viditelné mimo sestavení.<br />-Zásadní – Pokud změníte název parametru a metodu, která deklaruje ji lze zobrazit mimo sestavení.<br /><br /> Při vyvolání na lokální proměnné, která má stejný název jako pole:<br /><br /> – Pevná – Pokud pole nejsou viditelné mimo sestavení, bez ohledu na to, které provedete změnu.<br />– Pevná – Pokud změníte název místní proměnné a neměňte název pole.<br />-Dopadem na dřívější kód - li změnit název pole a jsou viditelné mimo sestavení.|  
  
## <a name="cause"></a>příčina  
 Metoda instance deklaruje parametr nebo místní proměnná, jejíž název odpovídá poli instance deklarovaného typu. K zachycení místní proměnné, které porušují pravidlo, musí být sestaveny testované sestavení s použitím informací o ladění a přidružené programového souboru databáze (PDB) musí být k dispozici.  
  
## <a name="rule-description"></a>Popis pravidla  
 Když se název pole instance shoduje, parametr nebo název místní proměnné, je přístup pole instance `this` (`Me` v [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) – klíčové slovo Pokud uvnitř těla metody. Při údržbě kódu, je snadné zapomenout tento rozdíl a předpokládá, že parametr/místní proměnná odkazuje na pole instance, což vede k chybám. To platí zejména pro delší těl metod.  
  
## <a name="how-to-fix-violations"></a>Jak vyřešit porušení  
 Chcete-li opravit porušení tohoto pravidla, přejmenujte parametr nebo proměnná nebo pole.  
  
## <a name="when-to-suppress-warnings"></a>Kdy potlačit upozornění  
 Nepotlačujte upozornění na toto pravidlo.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje dva porušení tohoto pravidla.  
  
 [!code-csharp[FxCop.Maintainability.VarMatchesField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/cs/FxCop.Maintainability.VarMatchesField.cs#1)]
 [!code-vb[FxCop.Maintainability.VarMatchesField#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.VarMatchesField/vb/FxCop.Maintainability.VarMatchesField.vb#1)]

