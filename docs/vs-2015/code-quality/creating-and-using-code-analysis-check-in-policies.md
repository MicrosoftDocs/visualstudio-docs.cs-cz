---
title: Vytváření a používání zásad vrácení se změnami analýzy kódu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5b2eb5059d5ec027654b1e4de7098c732e897088
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49238352"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Vytváření a používání zásad vrácení se změnami Analýzy kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při použití Team Foundation verze ovládacího prvku (TFVC), můžete vytvořit zásady analýzy kódu vrácení se změnami pro rozhraní .NET Framework a nativní (C/C++) projekty kódu v týmovém projektu. Zásady analýzy kódu vrácení se změnami můžete použít k řízení a zvýšení kvality kódu, který je vrácen do báze kódu.  
  
 Zásada je aplikována úspěšně, pokud je místní sestavení aktuální a na většině nedávných zdrojových souborech byla provedena analýza kódu. Minimálně musí pravidla analýzy kódu, které jsou povoleny v projektu kódu obsahovat stejná pravidla jako ty, které jsou definovány v zásadách vrácení se změnami týmového projektu. Pravidla, která je určená jako chyby v nastavení týmového projektu musí být také zadána jako chyby v projektu kódu  
  
> [!IMPORTANT]
>  Zásady vrácení se změnami analýzy kódu nelze použít pro webové projekty. Je možné použít pro projekty webových aplikací.  
  
 Zásady vrácení se změnami analýzy vytváření kódu s použitím nastavení týmového projektu [!INCLUDE[esprscc](../includes/esprscc-md.md)]. Zásady vrácení se změnami jsou zadány a vynucovány pro týmový projekt, ale nastavují spuštění analýzu kódu jsou konfiguraci a spuštění nad jednotlivými projekty kódu na místních vývojových počítačích. Tato část popisuje, jak určit zásady analýzy kódu vrácení se změnami pro týmový projekt a implementace vlastních zásad analýzy kódu pro spravovaný kód.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Postupy: Vytváření nebo aktualizace standardních zásad vracení se změnami Analýzy kódu](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)  
 Popisuje kroky, které používají nastavena a upravena zásada analýzy kódu pro týmový projekt.  
  
 [Implementace vlastních zásad vrácení se změnami pro spravovaný kód](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md)  
 Popisuje kroky, které používáte k vytvoření vlastního pravidla pro nastavení zásady vrácení se změnami týmového projektu a pro synchronizaci projektů kódu týmového projektu se zásadou vrácení se změnami.  
  
 [Kompatibilita verzí pro zásady vracení se změnami Analýzy kódu](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md)  
 Popisuje problémy s kompatibilitou vrácení se změnami analýzy kódu mezi verzemi [!INCLUDE[vstsLong](../includes/vstslong-md.md)].  
  
 [Postupy: Přizpůsobení slovníku Analýzy kódu](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
 Vysvětluje, jak přidat slova a tokeny do slovníku, který se odkazuje v pravidlech pojmenovávání analýzy kódu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Nastavení a vynucení bran kvality](http://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)  
  
 [Zvýšení kvality kódu použitím zásad vracení se změnami týmového projektu](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)



