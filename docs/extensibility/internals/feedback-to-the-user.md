---
title: Zpětná vazba uživateli | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 39ab61615ed00504259909339734ab7874a6dfc6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860367"
---
# <a name="feedback-to-the-user"></a>Zpětná vazba uživateli
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE), vizuální zpětnou vazbu týkající se dostupné funkce podle aktuálního výběru a globální výběr kontextu uživatele. V následující tabulce jsou uvedeny funkce, které jsou k dispozici v kontextech jiný výběr.  
  
|Kontext výběru|Dostupné funkce|  
|-----------------------|-----------------------------|  
|IDE – integrované vývojové prostředí|Globální|  
|Aktuální nastavení produktu|Specifické pro produkt|  
|Aktivní hierarchii|Konkrétní typ hierarchie|  
|Aktivní hierarchii položky|Konkrétní typ položku hierarchie|  
|Aktivní dokument|Konkrétní typ dokumentu|  
|Okno nejvyšší rozhraní více dokumentů (MDI)|Konkrétní typ okna|  
|Kontext aktuálního výběru|Konkrétní kontext výběru|  
  
 Pokud se pouze zařízení surface funkce zákazníci potřebují a nepřetržitě poskytovat konzistentní výběru a zpětná vazba místní prostředí, vám pomůže zjednodušit v integrovaném vývojovém prostředí. Při každém otevření okna v rozhraní IDE, platí následující pravidla:  
  
- Pokud se okno změní jeho výběr kontextu, je v okně, jasně označeny názor na výběr a **dynamická Nápověda** okno, pokud je vidět, se aktualizuje tak, aby odrážela aktuální kontext.  
  
- Pokud se okno změní kontext globálního výběru, všechny kontextové nabídky, okna aktivní hierarchii a záhlaví okna aplikace se aktualizují tak, aby odrážela aktuální kontext.  
  
- Okna by měl surface vlastnosti pro aktuální výběr v **vlastnosti** okno a volitelně také, zda se zobrazí, **stránky vlastností** dialogové okno.  
  
- Pokud okno není surface vlastnosti nebo změnit výběr globální kontext, názor na výběr by neměl zůstat v okně když už není aktivní okno v integrovaném vývojovém prostředí.  
  
- Všechna okna nástrojů konkrétní dokumenty by měly odrážet neustále aktivní dokument.  
  
- Nabídky, panely nástrojů a záhlaví okna aplikace by měly odrážet okno klienta nejvyššího rozhraní více dokumentů (MDI).  
  
  Například, když kód HTML zobrazení **webový formulář** webové aplikace Visual Basic je projekt otevřít, a uživatel vybere `<td>` značky, zpětná vazba je k dispozici v následujícím způsobem:  
  
- Výběr je uvedené v aktivní okno a reflektován v **vlastnosti** okna.  
  
- Konkrétní dokumenty **nástrojů** aktualizován, aby odrážel aktivní dokument.  
  
- **Editor** nástrojů a **tabulky** nabídky se zobrazí a aktualizuje záhlaví tak, aby odrážely okně webového formuláře.  
  
- Okno aktivní hierarchii, což je obvykle **Průzkumníka řešení**a jeho název panelu aktualizovat tak, aby odrážela aktuální kontext a kontextové **projektu** příkazy nabídky nyní budou vztahovat na aktivním webu Projekt aplikace.  
  
## <a name="see-also"></a>Viz také:  
 [Výběr a Měna v prostředí IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)   
 [Kontextové objekty výběru](../../extensibility/internals/selection-context-objects.md)   
 [Hierarchie a výběr](../../extensibility/internals/hierarchies-and-selection.md)