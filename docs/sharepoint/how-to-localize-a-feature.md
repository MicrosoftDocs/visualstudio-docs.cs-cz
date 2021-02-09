---
title: 'Postupy: Lokalizace funkce | Microsoft Docs'
description: Naučte se lokalizovat názvy a popisy funkcí na SharePointu tím, že nahradíte pevně kódované řetězcové hodnoty výrazy, které odkazují na lokalizované prostředky.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4a3c427f207f6aac9f6a827eb6c24b799d635b46
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913598"
---
# <a name="how-to-localize-a-feature"></a>Postupy: Lokalizace funkce
  Ve výchozím nastavení používají tituly a popisy funkcí pevně zakódované řetězcové hodnoty. Chcete-li lokalizovat název a popis funkce, nahraďte řetězce výrazy, které odkazují na lokalizované prostředky.

## <a name="localize-a-feature"></a>Lokalizace funkce

#### <a name="to-localize-a-feature"></a>Lokalizace funkce

1. V **Průzkumník řešení** otevřete místní nabídku uzlu **Feature1** a pak zvolte **Přidat prostředek funkce**.

2. V dialogovém okně **Přidat prostředek** , ze seznamu vyberte možnost **invariantní jazyk** jako jazykovou verzi pro soubor prostředků výchozí funkce jazyka.

3. Opakujte předchozí krok pro každý lokalizovaný jazyk a zvolte jazyky dle vašeho výběru pro lokalizované soubory prostředků funkce.

     Jsou vytvořeny samostatné soubory prostředků funkcí: jeden pro výchozí jazyk a jeden pro každý lokalizovaný jazyk, který chcete podporovat.

4. Otevřete všechny soubory prostředků v editoru prostředků a potom zadejte všechna ID řetězců a jejich hodnoty.

     Například ve výchozím souboru prostředků funkce zadejte ID řetězce s hodnotou **název funkce** a druhý **řetězec s** **popisem** s hodnotou **Moje Popis funkce**. U každého lokalizovaného souboru prostředků použijte stejné ID řetězců jako v prostředku výchozí funkce, ale zadejte lokalizované řetězce pro hodnoty.

5. Po zadání všech hodnot prostředku otevřete místní nabídku pro funkci (například *Feature1. Feature*) a pak zvolte možnost **Návrhář zobrazení** a otevřete funkci v Návrháři funkcí.

6. Chcete-li lokalizovat pole **název** a **Popis** ve funkci, použijte následující formát k zadání hodnot do jejich polí:

     `$Resources:`*ID řetězce*

     Zadejte například $Resources:**title** do pole **název funkce** a $Resources:**Popis** v poli **Popis funkce** .

     ID řetězců musí odpovídat hodnotám, které se používají v souborech prostředků.

7. Kliknutím na klávesu **F5** sestavíte a spustíte aplikaci.

8. V SharePointu otevřete nabídku **Akce webu** , zvolte **nastavení lokality** a potom v části **Akce webu** zvolte odkaz **Spravovat funkce webu** .

9. Ve službě SharePoint změňte jazyk zobrazení z výchozí hodnoty.

     Lokalizovaný název a popis funkce se zobrazí v aplikaci. Chcete-li zobrazit lokalizované prostředky, musí mít server SharePoint nainstalovanou jazykovou sadu, která odpovídá jazykové verzi souboru prostředků.

## <a name="see-also"></a>Viz také
- [Lokalizace řešení služby SharePoint](../sharepoint/localizing-sharepoint-solutions.md)
- [Postupy: Přidání souboru prostředků](../sharepoint/how-to-add-a-resource-file.md)
- [Postupy: lokalizace značek ASPX](../sharepoint/how-to-localize-aspx-markup.md)
- [Postupy: Lokalizace kódu](../sharepoint/how-to-localize-code.md)
