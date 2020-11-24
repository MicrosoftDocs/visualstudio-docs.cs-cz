---
title: Řešení potíží se šablonami projektů a šablonami položek
description: Naučte se řešit potíže se šablonami, když se nepodaří načíst ve vývojovém prostředí.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 42dc34d846f37ed1d7655d6758d045b2db7187d9
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596843"
---
# <a name="how-to-troubleshoot-templates"></a>Postupy: řešení problémů se šablonami

Pokud se šablonu nepovede načíst ve vývojovém prostředí, existuje několik způsobů, jak tento problém najít.

## <a name="validate-the-vstemplate-file"></a>Ověřit soubor vstemplate

::: moniker range="vs-2017"

Pokud soubor *vstemplate* v šabloně neodpovídá schématu šablony sady Visual Studio, šablona se nemusí zobrazit v dialogovém okně **Nový projekt** .

::: moniker-end

::: moniker range=">=vs-2019"

Pokud soubor *vstemplate* v šabloně neodpovídá schématu šablony sady Visual Studio, šablona se nemusí zobrazit v dialogovém okně, ve kterém vytvoříte nové projekty.

::: moniker-end

### <a name="to-validate-the-vstemplate-file"></a>Ověření souboru vstemplate

1. Vyhledejte soubor *. zip* , který obsahuje šablonu.

1. Extrahujte soubor *. zip* .

1. V nabídce **soubor** v aplikaci Visual Studio vyberte možnost **otevřít**  >  **soubor**.

1. Vyberte soubor *vstemplate* pro šablonu a zvolte **otevřít**.

1. Ověřte, zda soubor XML souboru *vstemplate* dodržuje schéma šablony. Další informace o schématu *vstemplate* naleznete v tématu [reference ke schématu šablony](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Chcete-li získat podporu technologie IntelliSense při vytváření souboru *vstemplate* , přidejte `xmlns` do `VSTemplate` prvku atribut a přiřaďte mu hodnotu `http://schemas.microsoft.com/developer/vstemplate/2005` .

1. Uložte a zavřete soubor *vstemplate* .

1. Vyberte soubory zahrnuté do šablony, klikněte pravým tlačítkem myši a zvolte **Odeslat do**  >  **komprimované složky (ZIP)**. Soubory, které jste vybrali, se komprimují do souboru *zip* .

1. Nový soubor *. zip* umístěte do stejného adresáře jako starý soubor *. zip* .

1. Odstraňte extrahované soubory šablon a starý soubor template *. zip* .

## <a name="enable-diagnostic-logging"></a>Povolení protokolování diagnostiky

Můžete povolit protokolování diagnostiky pro zjišťování šablon podle kroků v tématu [řešení potíží se zjišťováním šablon (rozšiřitelnost)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Viz také

- [Řešení potíží se zjišťováním šablon (rozšiřitelnost)](../extensibility/troubleshooting-template-discovery.md)
- [Přizpůsobení šablon](../ide/customizing-project-and-item-templates.md)
- [Vytváření šablon projektů a položek](../ide/creating-project-and-item-templates.md)
- [Odkaz na schéma šablony](../extensibility/visual-studio-template-schema-reference.md)
