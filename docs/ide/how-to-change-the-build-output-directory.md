---
title: 'Postupy: Změna výstupního adresáře sestavení'
description: Zjistěte, jak můžete určit umístění výstupu generovaného vaším projektem podle konfigurace (pro ladění, vydání nebo obojí).
ms.custom: SEO-VS-2020
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 792175d7d2c168f75d20bce86675a1fcd8c47899
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875533"
---
# <a name="how-to-change-the-build-output-directory"></a>Postupy: Změna výstupního adresáře sestavení

Můžete určit umístění výstupu generovaného vaším projektem podle konfigurace (pro ladění, vydání nebo obojí).

## <a name="change-the-build-output-directory"></a>Změna výstupního adresáře sestavení

1. Chcete-li otevřít stránky vlastností projektu, klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte možnost **vlastnosti**.

2. Vyberte příslušnou kartu na základě typu projektu:

   - V jazyce C# vyberte kartu **sestavení** .
   - Pro Visual Basic vyberte kartu **kompilovat** .
   - V případě C++ nebo JavaScript vyberte kartu **Obecné** .

3. V rozevíracím seznamu konfigurace v horní části vyberte konfiguraci, jejíž umístění výstupního souboru chcete změnit (**ladění**, **vydání** nebo **všechny konfigurace**).

4. Najít položku výstupní cesty na stránce, která &mdash; se liší v závislosti na typu projektu:

   - **Výstupní cesta** pro projekty v jazyce C# a JavaScript
   - **Výstupní cesta k sestavení** pro projekty Visual Basic
   - **Výstupní adresář** pro projekty Visual C++

   Zadejte cestu k vygenerování výstupu (absolutní nebo relativní ke kořenovému adresáři projektu), nebo klikněte na tlačítko **Procházet** a přejděte k této složce.

   ![Vlastnost výstupní cesty pro projekt C# v jazyce Visual Studio](media/output-path.png)
   
   > [!NOTE]
   > Některé projekty budou standardně zahrnovat rozhraní a modul runtime v cestě sestavení. Pokud to chcete změnit, klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení**, vyberte **Upravit soubor projektu** a přidejte následující:
   > ```xml
   > <PropertyGroup>
   >   <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
   >   <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
   > </PropertyGroup>
   > ```

> [!TIP]
> Pokud výstup není generován do umístění, které jste určili, ujistěte se, že vytváříte odpovídající konfiguraci (například **ladění** nebo **vydání**) tak, že ji vyberete v panelu nabídek aplikace Visual Studio.
>
> ![Výběr konfigurace sestavení v aplikaci Visual Studio 2019](media/build-configuration-chooser.png)

## <a name="see-also"></a>Viz také

- [Stránka sestavení, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Obecná stránka vlastností (projekt)](/cpp/build/reference/general-property-page-project)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
