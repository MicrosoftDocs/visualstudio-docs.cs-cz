---
title: Poradce při potížích s načítáním šablony a položky projektu
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1bef6a460f1a59823930597565b955b591ab48a0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591382"
---
# <a name="how-to-troubleshoot-templates"></a>Postup: Poradce při potížích se šablonami

Pokud se šablona nenačte ve vývojovém prostředí, existuje několik způsobů, jak problém vyhledat.

## <a name="validate-the-vstemplate-file"></a>Ověření souboru vstemplate

::: moniker range="vs-2017"

Pokud soubor *vstemplate* v šabloně nedodržuje schéma šablony sady Visual Studio, nemusí se šablona zobrazit v dialogovém okně **Nový projekt.**

::: moniker-end

::: moniker range=">=vs-2019"

Pokud soubor *vstemplate* v šabloně nedodržuje schéma šablony sady Visual Studio, nemusí se šablona zobrazit v dialogovém okně, ve kterém vytváříte nové projekty.

::: moniker-end

### <a name="to-validate-the-vstemplate-file"></a>Ověření souboru vstemplate

1. Vyhledejte soubor *ZIP* obsahující šablonu.

1. Extrahujte soubor *ZIP.*

1. V nabídce **Soubor** v sadě Visual Studio zvolte **Otevřít** > **soubor**.

1. Vyberte soubor *vstemplate* pro šablonu a zvolte **Otevřít**.

1. Ověřte, zda xml souboru *vstemplate* dodržuje schéma šablony. Další informace o schématu *vstemplate* naleznete v [tématu odkaz na schéma šablony](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Chcete-li získat podporu Technologie IntelliSense při vytváření `xmlns` souboru `VSTemplate` *vstemplate,* přidejte `http://schemas.microsoft.com/developer/vstemplate/2005`k prvku atribut a přiřaďte mu hodnotu .

1. Uložte a zavřete soubor *vstemplate.*

1. Vyberte soubory obsažené v šabloně, klikněte pravým tlačítkem myši a zvolte **Odeslat do** > **komprimované (zip) složky**. Vybrané soubory jsou komprimovány do souboru *ZIP.*

1. Umístěte nový soubor *ZIP* do stejného adresáře jako starý soubor *ZIP.*

1. Odstraňte extrahované soubory šablon a starý soubor *ZIP* šablony.

## <a name="enable-diagnostic-logging"></a>Povolení protokolování diagnostiky

Protokolování diagnostiky pro zjišťování šablony můžete povolit podle kroků v [části Poradce při potížích s zjišťováním šablony (rozšiřitelnost)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Viz také

- [Poradce při potížích s zjišťováním šablony (rozšiřitelnost)](../extensibility/troubleshooting-template-discovery.md)
- [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)
- [Vytvoření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Odkaz na schéma šablony](../extensibility/visual-studio-template-schema-reference.md)
