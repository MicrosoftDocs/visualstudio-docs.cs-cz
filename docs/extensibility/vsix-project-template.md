---
title: Šablona projektu VSIX | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploy packages
- publish extension
ms.assetid: b6c82167-e2a5-4cff-8c8b-2d72e2a9092c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74791a77ee1c720fb60876a1efa6bd58fa94f68b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697926"
---
# <a name="vsix-project-template"></a>Šablona projektu VSIX

Šablonu Projektu VSIX můžete použít k zabalení jednoho nebo více rozšíření sady Visual Studio v projektu VSIX a potom publikovat balíček na webu [Visual Studio Marketplace.](https://marketplace.visualstudio.com/)

 Nasazení VSIX podporuje vspackages, sestavení, mef komponenty, šablony projektů, šablony položek, ovládací prvky panelu nástrojů a vlastní typy rozšíření.

> [!NOTE]
> Chcete-li použít projekty VSIX, je nutné nainstalovat sady Visual Studio SDK. Další informace o sadě Visual Studio SDK naleznete v [tématu Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="where-to-find-the-vsix-project-template"></a>Kde najít šablonu projektu VSIX

Šablona projektu VSIX je k dispozici v dialogovém okně **Nový projekt** vyhledáním "vsix".  K dispozici je verze jazyka C# a visual basic.

> [!TIP]
> Měli byste se ujistit, že rozhraní .NET Framework 4.5 nebo vyšší je zadáno v rozevíracím seznamu v horní části dialogového okna **Nový projekt.**

## <a name="uses-of-the-vsix-project-template"></a>Použití šablony projektu VSIX

Šablona projektu VSIX má dvě hlavní použití:

- Nasazení šablon projektů, šablon položek a rozšíření.

- Chcete-li zabalit výstupy více rozšíření do jednoho balíčku nasazení.

## <a name="packaging-an-extension-in-an-empty-vsix-project"></a>Balení rozšíření v prázdném projektu VSIX

Můžete zabalit existující rozšíření nebo rozšíření, které ještě nemá podporu VSIX, zabalením do prázdného projektu VSIX. Rozšíření, které má být zabaleno, musí být typu, který je podporován [schématem VSIX](../extensibility/vsix-extension-schema-2-0-reference.md).

### <a name="to-package-an-extension-by-using-a-vsix-project"></a>Chcete-li balíček rozšíření pomocí projektu VSIX

1. Vytvořte projekty, které tvoří rozšíření.

2. Vytvořte projekt VSIX pomocí šablony **projektu VSIX.**

    *Source.extension.vsixmanifest* otevře v **Návrhář manifestu**.

3. Na kartě **Datové zdroje** zvolte **tlačítko Nový.**

    Zobrazí se dialogové okno **Přidat nový datový** zdroj.

4. V seznamu **Typ** zvolte typ rozšíření, které chcete přidat.

5. Chcete-li přidat prvek rozšíření nebo obsahu, který je součástí aktuálního řešení (například šablona položky nebo kompilované sestavení), proveďte následující kroky:

   1. V seznamu **Zdroj** zvolte **Projekt A v aktuálním řešení**.

   2. V seznamu **Projekt** zvolte název rozšíření.

   3. Do pole **Vložit do této složky** zadejte název složky, do které chcete datový zdroj vložit, a pak zvolte tlačítko **OK.**

6. Chcete-li přidat prvek rozšíření nebo obsahu, který není součástí aktuálního řešení, proveďte následující kroky:

   1. V seznamu **Zdroj** zvolte **Soubor v souborovém systému**.

   2. Do pole **Cesta** zadejte úplnou cestu k kompilovanému nebo komprimovanému souboru rozšíření nebo pomocí tlačítka **Procházet** soubor projděte.

   3. Do pole **Vložit do této složky** zadejte název složky, do které chcete datový zdroj vložit, a pak zvolte tlačítko **OK.**

7. Pokud chcete, aby váš balíček obsahoval další rozšíření, přidejte je stejným způsobem.

8. Sestavte řešení.

    [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]vytvoří soubor *.vsix,* který obsahuje soubor manifestu VSIX, soubor *[Content_Types] XML* a všechny datové zdroje rozšíření, které jste přidali do projektu.

## <a name="see-also"></a>Viz také

- [Odkaz na schéma rozšíření VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Vyhledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
