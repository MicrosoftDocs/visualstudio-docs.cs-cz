---
title: 'Postupy: Změna výstupního adresáře sestavení'
ms.date: 05/15/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 493de227174b60b4834c2732ddbf16a5586fa49e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71238189"
---
# <a name="how-to-change-the-build-output-directory"></a>Postupy: Změna výstupního adresáře sestavení

Můžete určit umístění výstupu generovaného vaším projektem podle konfigurace (pro ladění, vydání nebo obojí).

## <a name="change-the-build-output-directory"></a>Změna výstupního adresáře sestavení

1. Chcete-li otevřít stránky vlastností projektu, klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení** a vyberte možnost **vlastnosti**.

2. Vyberte příslušnou kartu na základě typu projektu:

   - V případě klikněte na kartu **sestavení.** C#
   - Pro Visual Basic vyberte kartu **kompilovat** .
   - Pro C++ nebo JavaScript vyberte kartu **Obecné** .

3. V rozevíracím seznamu konfigurace v horní části vyberte konfiguraci, jejíž umístění výstupního souboru chcete změnit (**ladění**, **vydání**nebo **všechny konfigurace**).

4. Najít položku výstupní cesty na stránce&mdash;, která se liší v závislosti na typu projektu:

   - **Výstupní cesta** pro C# projekty a projekty JavaScriptu
   - **Výstupní cesta k sestavení** pro projekty Visual Basic
   - **Výstupní adresář** pro vizuální C++ projekty

   Zadejte cestu k vygenerování výstupu (absolutní nebo relativní ke kořenovému adresáři projektu), nebo klikněte na tlačítko **Procházet** a přejděte k této složce.

   ![Vlastnost výstupní cesty pro projekt sady Visual C# Studio](media/output-path.png)
   
   > [!NOTE]
   > Některé projekty budou standardně zahrnovat rozhraní a modul runtime v cestě sestavení. Pokud to chcete změnit, klikněte pravým tlačítkem myši na uzel projektu v **Průzkumník řešení**, vyberte **Upravit soubor projektu**a přidejte následující:
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

## <a name="see-also"></a>Viz také:

- [Stránka sestavení, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Obecná stránka vlastností (projekt)](/cpp/build/reference/general-property-page-project)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
