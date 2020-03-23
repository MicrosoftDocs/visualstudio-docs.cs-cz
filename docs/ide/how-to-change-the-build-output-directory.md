---
title: 'Postup: Změna výstupního adresáře sestavení'
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
ms.openlocfilehash: 37342796f2dd94138136bb837cf6007d19d350c4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114265"
---
# <a name="how-to-change-the-build-output-directory"></a>Postup: Změna výstupního adresáře sestavení

Můžete určit umístění výstupu generovaného projektem na základě konfigurace (pro ladění, vydání nebo obojí).

## <a name="change-the-build-output-directory"></a>Změna výstupního adresáře sestavení

1. Chcete-li otevřít stránky vlastností projektu, klepněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení** a vyberte **příkaz Vlastnosti**.

2. Vyberte příslušnou kartu na základě typu projektu:

   - V souboru C# vyberte kartu **Sestavení.**
   - V jazyce Visual Basic vyberte kartu **Kompilace.**
   - V jazyce C++ nebo JavaScriptu vyberte kartu **Obecné.**

3. V rozevíracím přehledu konfigurace v horní části zvolte konfiguraci, jejíž umístění výstupního souboru chcete změnit (**Ladění**, **Vydání**nebo **Všechny konfigurace**).

4. Najděte položku výstupní&mdash;cesty na stránce, která se liší v závislosti na typu projektu:

   - **Výstupní cesta** pro projekty Jazyka C# a JavaScriptu
   - **Vytvořit výstupní cestu** pro projekty jazyka Visual Basic
   - **Výstupní adresář** pro projekty visual c++

   Zadejte cestu ke generování výstupu (absolutní nebo relativní k kořenovému adresáři projektu) nebo zvolte **Procházet** a procházejte do této složky.

   ![Vlastnost výstupní cesty pro projekt jazyka Visual Studio C#](media/output-path.png)
   
   > [!NOTE]
   > Některé projekty budou ve výchozím nastavení zahrnovat rozhraní framework a runtime v cestě sestavení. Chcete-li to toto změnit, klepněte pravým tlačítkem myši na uzel projektu v **Průzkumníku řešení**, vyberte **příkaz Upravit soubor projektu**a přidejte následující:
   > ```xml
   > <PropertyGroup>
   >   <AppendTargetFrameworkToOutputPath>false</AppendTargetFrameworkToOutputPath>
   >   <AppendRuntimeIdentifierToOutputPath>false</AppendRuntimeIdentifierToOutputPath>
   > </PropertyGroup>
   > ```

> [!TIP]
> Pokud výstup není generován do zadaného umístění, ujistěte se, že vytváříte odpovídající konfiguraci (například **Ladění** nebo **Vydání)** výběrem na panelu nabídek sady Visual Studio.
>
> ![Výběr konfigurace sestavení ve Visual Studiu 2019](media/build-configuration-chooser.png)

## <a name="see-also"></a>Viz také

- [Stránka sestavení, Návrhář projektu (C#)](../ide/reference/build-page-project-designer-csharp.md)
- [Stránka Obecná vlastnost (projekt)](/cpp/build/reference/general-property-page-project)
- [Kompilace a sestavení](../ide/compiling-and-building-in-visual-studio.md)
