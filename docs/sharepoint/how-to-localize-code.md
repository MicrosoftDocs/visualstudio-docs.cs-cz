---
title: 'Postupy: lokalizace kódu | Microsoft Docs'
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
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d170906a66ffaaa0e73d4d7d236c8f41290abe55
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120267"
---
# <a name="how-to-localize-code"></a>Postupy: lokalizace kódu
  Nelokalizované kód používá pevně zakódovaný řetězcové hodnoty. Na kód řetězce pro lokalizaci, je nahradit volání <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>, což je metoda, která odkazuje na lokalizované prostředky.  
  
## <a name="localize-code"></a>Lokalizace kódu  
  
#### <a name="to-localize-code"></a>Chcete-li lokalizace kódu  
  
1.  V **Průzkumníku řešení**, otevřete místní nabídku pro položku projektu a potom zvolte **přidat** > **modulu**.  
  
     Vyberte **souboru prostředků** šablony.  
  
    > [!NOTE]  
    >  Ujistěte se, že soubor prostředků přidat do položky projektu služby SharePoint, aby vlastnost typ nasazení k dispozici. Tato vlastnost se vyžaduje později v tomto postupu.  
  
2.  Zadejte název zvoleného s příponou souboru prostředků jazyka výchozí *RESX* rozšíření, jako například *MyAppResources.resx*.  
  
3.  Opakujte kroky 1 a 2, pokud chcete přidat soubory samostatné prostředků do položky projektu služby SharePoint: jeden pro každou lokalizované jazyk.  
  
     Použijte stejný základní název pro každý soubor lokalizovaný prostředek, ale přidat ID jazykovou verzi. Například název němčina lokalizované prostředků *MyAppResources.de DE.resx*.  
  
4.  Otevřete soubor každý prostředek a přidejte lokalizované řetězce. Použijte stejný řetězec ID do každého souboru.  
  
5.  Změňte hodnotu **typ nasazení** vlastnost souborů prostředků se **AppGlobalResource** způsobí každý soubor pro nasazení do složky App_GlobalResources serveru.  
  
6.  Ponechte hodnotu **akce sestavení** vlastnosti každého souboru jako **vložený prostředek**.  
  
     Vložené prostředky jsou zkompilovány do projektu knihovny DLL.  
  
7.  Sestavte projekt a vytvořte prostředek satelitní knihovny DLL.  
  
8.  V **návrháře balíčků**, vyberte **Upřesnit** a pak přidejte satelitní sestavení.  
  
9. V **umístění** pole, předřazení ID složku jazykovou verzi pro cestu k umístění, jako například *de-DE\\\<název položky projektu >. resources.dll*.  
  
10. Pokud vaše řešení neodkazuje již System.Web sestavení, přidejte odkaz na jeho a přidejte direktivu ve svém kódu pro <xref:System.Web>.  
  
11. Vyhledejte všechny řetězce pevně zakódovaná ve vašem kódu, které jsou viditelné pro uživatele, například textu uživatelského rozhraní, chyb a text zprávy. Nahraďte volání <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> metoda pomocí následující syntaxe:  
  
    ```csharp  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. Vyberte **F5** klíč sestavení a spuštění aplikace.  
  
13. Ve službě SharePoint změňte z výchozí jazyk zobrazení.  
  
     Lokalizované řetězce se zobrazí v aplikaci. Pokud chcete zobrazit lokalizované prostředky, musí mít serveru SharePoint jazyková sada nainstalovaná odpovídající jazykové verze souboru prostředků.  
  
## <a name="see-also"></a>Viz také:
 [Lokalizace řešení služby SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Postupy: lokalizace funkce](../sharepoint/how-to-localize-a-feature.md)   
 [Postupy: lokalizace značek ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Postupy: Přidání zdrojového souboru](../sharepoint/how-to-add-a-resource-file.md)  

