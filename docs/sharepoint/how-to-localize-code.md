---
title: 'Postupy: Lokalizace kódu | Microsoft Docs'
description: Naučte se lokalizovat kód ve službě SharePoint nahrazením pevně kódovaných řetězců pomocí volání GetGlobalResourceObject, metody, která odkazuje na lokalizované prostředky.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2cbe38c55b92514954cc3487544fed89d68cc4dc
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304581"
---
# <a name="how-to-localize-code"></a>Postupy: Lokalizace kódu
  Nemístní kód používá pevně kódované řetězcové hodnoty. Chcete-li lokalizovat řetězce kódu, nahraďte je voláními <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> , což je metoda, která odkazuje na lokalizované prostředky.

## <a name="localize-code"></a>Lokalizovat kód

#### <a name="to-localize-code"></a>Lokalizace kódu

1. V **Průzkumník řešení** otevřete místní nabídku pro položku projektu a pak zvolte **Přidat**  >  **modul**.

     Vyberte šablonu **souboru prostředků** .

    > [!NOTE]
    > Nezapomeňte přidat soubor prostředků do položky projektu služby SharePoint, aby byla k dispozici vlastnost typ nasazení. Tato vlastnost je povinná později v tomto postupu.

2. Pojmenujte soubor prostředků výchozího jazyka názvem vaší volby, který je připojený s příponou *. resx* , jako je *MyAppResources. resx*.

3. Opakováním kroků 1 a 2 přidejte samostatné soubory prostředků do položky projektu služby SharePoint: jeden pro každý lokalizovaný jazyk.

     Použijte stejný základní název pro každý lokalizovaný soubor prostředků, ale přidejte ID jazykové verze. Například pojmenujte německý lokalizovaný prostředek *MyAppResources.de-de. resx*.

4. Otevřete všechny soubory prostředků a přidejte lokalizované řetězce. V každém souboru použijte stejné ID řetězců.

5. Změňte hodnotu vlastnosti **typ nasazení** každého souboru prostředků na **AppGlobalResource** , aby byl každý soubor nasazen do složky App_GlobalResources serveru.

6. Ponechte hodnotu vlastnosti **Akce sestavení** každého souboru jako **vložený prostředek**.

     Vložené prostředky jsou kompilovány do knihovny DLL projektu.

7. Sestavte projekt pro vytvoření prostředků satelitních knihoven DLL.

8. V **Návrháři balíčků** zvolte kartu **Upřesnit** a pak přidejte satelitní sestavení.

9. V poli **umístění** předřaďte složku ID jazykové verze na cestu k umístění, například *.resources.dllde-de \\ \<Project Item Name>*.

10. Pokud vaše řešení ještě neodkazuje na sestavení System. Web, přidejte na něj odkaz a přidejte do kódu direktivu do <xref:System.Web> .

11. Vyhledejte všechny pevně kódované řetězce v kódu, které jsou viditelné pro uživatele, například text uživatelského rozhraní, chyby a text zprávy. Nahraďte je voláním <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> metody pomocí následující syntaxe:

    ```csharp
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")
    ```

12. Kliknutím na klávesu **F5** sestavíte a spustíte aplikaci.

13. Ve službě SharePoint změňte jazyk zobrazení z výchozí hodnoty.

     Lokalizované řetězce se zobrazí v aplikaci. Chcete-li zobrazit lokalizované prostředky, musí mít server SharePoint nainstalovanou jazykovou sadu, která odpovídá jazykové verzi souboru prostředků.

## <a name="see-also"></a>Viz také
- [Lokalizace řešení služby SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Postupy: Lokalizace funkce](../sharepoint/how-to-localize-a-feature.md)
- [Postupy: lokalizace značek ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Postupy: Přidání souboru prostředků](../sharepoint/how-to-add-a-resource-file.md)
