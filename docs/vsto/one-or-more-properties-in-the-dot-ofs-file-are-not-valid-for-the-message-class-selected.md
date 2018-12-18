---
title: Jedna nebo více vlastností v souboru .ofs nejsou pro vybranou třídu zpráv platné.
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.NewFormRegionWizard.OFSPropertyError
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cfae8533337bbe18c89dbb670fb58a0c89c6c54c
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692496"
---
# <a name="one-or-more-properties-in-the-ofs-file-are-not-valid-for-the-message-class-selected"></a>Jedna nebo více vlastností v souboru .ofs nejsou pro vybranou třídu zpráv platné.
  Tato chyba se zobrazí, když importujete oblasti formuláře navržené v aplikaci Outlook, ale nejsou kompatibilní s třídami zpráv, které jste vybrali na poslední stránce minimálně jedno pole v oblasti formuláře **nové oblasti formuláře** průvodce.  

Například můžete vybrat **úloh (IPM. Úlohy)** na poslední stránce **nové oblasti formuláře** průvodce. Pokud má oblasti formuláře **podnikání** pole, dostanete této chybě, protože úloha nemá adresu firmy. Proto **podnikání** pole není kompatibilní s `IPM.Task` třída zprávy.  
  
 Můžete vybrat **úloh (IPM. Úlohy)** na poslední stránce **nové oblasti formuláře** průvodce. Pokud má oblasti formuláře **podnikání** pole, dostanete této chybě, protože úloha nemá adresu firmy. Proto **podnikání** pole není kompatibilní s `IPM.Task` třída zprávy.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Na poslední stránce **nové oblasti formuláře** průvodce, vyberte třídu zpráv, který je kompatibilní s pole v oblasti formuláře.  
  
-   V Návrháři formulářů v aplikaci Outlook odeberte pole, která nejsou kompatibilní s třídami zpráv. Odebrat pole, které chcete na poslední stránce vyberte **nové oblasti formuláře** průvodce.  
  
## <a name="see-also"></a>Viz také:  
 [Návod: Importujte oblasti formuláře navržené v aplikaci Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  