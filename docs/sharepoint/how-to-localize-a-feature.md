---
title: 'Postupy: lokalizace funkce | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c143016aaec81c65c118923ff9513bb4607353dc
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120192"
---
# <a name="how-to-localize-a-feature"></a>Postupy: lokalizace funkce
  Ve výchozím nastavení použijte funkci názvy a popisy pevně řetězcové hodnoty. Lokalizace funkce nadpis a popis, nahraďte řetězce výrazy, které odkazují na lokalizované prostředky.  
  
## <a name="localize-a-feature"></a>Lokalizace funkce  
  
#### <a name="to-localize-a-feature"></a>Chcete-li lokalizace funkce  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídku pro **Feature1** uzel a potom zvolte **přidat prostředek funkce**.  
  
2.  V **přidat prostředek** dialogovém okně vyberte **neutrální jazyk** ze seznamu jako jazykovou verzi pro výchozí jazyk funkce zdrojový soubor.  
  
3.  Opakujte předchozí krok pro jednotlivé lokalizované jazyky volba jazyků podle svého výběru pro funkci lokalizované soubory prostředků.  
  
     Soubory prostředků samostatné funkce vytvářejí: jeden pro výchozí jazyk a jeden pro jednotlivé lokalizované jazyk, který chcete podporovat.  
  
4.  Každý prostředek soubor otevřete v editoru prostředků a potom zadejte všechny identifikátory řetězec a jejich hodnot.  
  
     Například výchozí funkce zdrojový soubor, zadejte řetězec ID **název** s hodnotou **Moje funkce Title**, a druhý řetězec ID **popis** s hodnotou **Můj popis funkce**. Pro každý soubor lokalizovaný prostředek použít stejné ID používaná v prostředku funkce výchozí řetězec, ale zadat lokalizované řetězce pro hodnoty.  
  
5.  Po zadání všech hodnot prostředků, otevřete místní nabídku pro funkci (například *Feature1.feature*) a potom zvolte **Návrhář zobrazení** funkce Otevřít v Návrháři funkce.  
  
6.  O lokalizaci **název** a **popis** pole ve funkci, použijte následující formát pro zadání hodnot v jejich polí:  
  
     `$Resources:` *Řetězec ID*  
  
     Zadejte například $Resources:**název** v **název funkce** pole a $Resources:**popis** v **popis funkce** pole .  
  
     Řetězec ID se musí shodovat ty, které se používají v souborech prostředků.  
  
7.  Vyberte **F5** klíč sestavení a spuštění aplikace.  
  
8.  Ve službě SharePoint, otevřete **Akce webu** nabídce zvolte **nastavení lokality**a pak na **Akce webu** vyberte **spravovat funkce webu** odkaz.  
  
9. Ve službě SharePoint změňte z výchozí jazyk zobrazení.  
  
     Funkce lokalizovaný název a popis se zobrazí v aplikaci. Pokud chcete zobrazit lokalizované prostředky, musí mít serveru SharePoint jazyková sada nainstalovaná odpovídající jazykové verze souboru prostředků.  
  
## <a name="see-also"></a>Viz také:
 [Lokalizace řešení služby SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Postupy: Přidání zdrojového souboru](../sharepoint/how-to-add-a-resource-file.md)   
 [Postupy: lokalizace značek ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Postupy: lokalizace kódu](../sharepoint/how-to-localize-code.md)  
  
