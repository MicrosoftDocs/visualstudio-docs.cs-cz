---
title: Zabezpečení textových šablon | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, security
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 65b4b6616921dae0abb0bb54316d8b8262d1f652
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214679"
---
# <a name="security-of-text-templates"></a>Zabezpečení textových šablon
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Textové šablony mají následující aspekty zabezpečení:  
  
-   Textové šablony jsou citlivé na libovolný kód vložení.  
  
-   Pokud mechanismus, který hostitel používá k vyhledání procesoru direktiv není zabezpečený, může spustit škodlivý procesor direktiv.  
  
## <a name="arbitrary-code"></a>Libovolný kód  
 Při psaní šablonu možné vložit jakýkoli kód v rámci \<## > značky. To umožňuje libovolného kódu být spuštěn přímo z textové šablony.  
  
 Ujistěte se, že získání šablony z důvěryhodných zdrojů. Ujistěte se, že varování koncové uživatele vaší aplikace není pro spouštění šablon, které nepochází z důvěryhodných zdrojů.  
  
## <a name="malicious-directive-processor"></a>Škodlivý procesoru direktiv  
 Modul šablon textu pracuje s hostiteli transformaci a jeden nebo více procesorů pro direktivy transformace textu šablony do výstupního souboru. Další informace najdete v tématu [proces transformace textových šablon](../modeling/the-text-template-transformation-process.md).  
  
 Pokud mechanismus, který hostitel používá k vyhledání procesoru direktiv není bezpečná, spustí se nebezpečí spuštění škodlivého procesor direktiv. Škodlivý procesor direktiv může poskytnout kód, který je spuštěn v `FullTrust` režimu při spuštění šablony. Pokud jste vytvořili hostitele transformace vlastní textových šablon, je nutné použít mechanismus zabezpečeného například registr pro modul najít procesory direktiv.



