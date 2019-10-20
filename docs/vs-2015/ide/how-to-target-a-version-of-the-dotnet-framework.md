---
title: 'Postupy: cílení na verzi .NET Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 53
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7aae21e2c959939262b88db3b90367c4860d8a74
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670622"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Postupy: Cílení na verzi rozhraní .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument popisuje, jak při vytvoření projektu cílit na určitou verzi rozhraní .NET Framework a jak změnit cílenou verzi v existujícím projektu v jazyce Visual Basic, Visual C# nebo Visual F#.

> [!IMPORTANT]
> Informace o tom, jak změnit cílovou verzi pro C++ projekty, naleznete v tématu [How to: Modify The Target Framework and sada nástrojů Platform](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).

 **V tomto tématu**

- [Cílení na verzi při vytváření projektu](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)

- [Změna cílové verze](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)

## <a name="bkmk_new"></a>Cílení na verzi při vytváření projektu
 Šablony, které můžete použít při vytváření projektu, jsou určeny verzí rozhraní .NET Framework, na kterou cílíte.

> [!NOTE]
> V edicích Express sady Visual Studio je nutné nejprve vytvořit projekt a potom změnit cílovou [verzi](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing) , která je popsána dále v tomto tématu.

#### <a name="to-target-a-version-when-you-create-a-project"></a>Cílení na určitou verzi při vytváření projektu

1. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.

2. V seznamu v horní části dialogového okna **Nový projekt** vyberte verzi .NET Framework, na kterou chcete projekt cílit.

    > [!NOTE]
    > Se sadou Visual Studio se obvykle instaluje jen jedna verze rozhraní .NET Framework. Pokud chcete cílit na jinou verzi, je nejprve třeba zkontrolovat, zda je nainstalovaná. Viz [Přehled cílení na více platforem sady Visual Studio](../ide/visual-studio-multi-targeting-overview.md).

3. V seznamu nainstalovaných šablon zvolte typ projektu, který chcete vytvořit, zadejte název projektu a pak klikněte na tlačítko **OK** .

     V seznamu šablon jsou uvedeny pouze projekty, které jsou podporovány vámi vybranou verzí rozhraní .NET Framework.

## <a name="bkmk_existing"></a>Změna cílové verze
 Pomocí tohoto postupu můžete změnit cílovou verzi .NET Framework v projektu Visual Basic, vizuálu C#nebo Visual. F#

#### <a name="to-change-the-targeted-version"></a>Změna cílené verze

1. V **Průzkumník řešení**otevřete místní nabídku pro projekt, který chcete změnit, a poté zvolte možnost **vlastnosti**.

     ![Vlastnosti Průzkumník řešení sady Visual Studio](../ide/media/vs-slnexplorer-properties.png "vs_slnExplorer_Properties")

    > [!IMPORTANT]
    > Informace o tom, jak změnit cílovou verzi pro C++ projekty, naleznete v tématu [How to: Modify The Target Framework and sada nástrojů Platform](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).

2. V levém sloupci okna Vlastnosti vyberte kartu **aplikace** .

     ![Karta aplikace vlastností aplikace Visual Studio](../ide/media/vs-slnexplorer-properties-applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")

    > [!NOTE]
    > Po vytvoření aplikace pro Windows Store nemůžete změnit cílovou verzi buď Windows, nebo .NET Framework.

3. V seznamu **cílové rozhraní** vyberte požadovanou verzi.

4. V dialogovém okně ověření, které se zobrazí, klikněte na tlačítko **Ano** .

     Projekt se uvolní. Až se znovu načte, bude cílit na verzi rozhraní .NET Framework, kterou jste vybrali.

    > [!NOTE]
    > Pokud váš kód obsahuje odkazy na jinou verzi rozhraní .NET Framework, než na kterou cílíte, mohou se při kompilaci či spuštění kódu zobrazit chybové zprávy. Chcete-li tyto chyby vyřešit, je třeba upravit odkazy. Další informace najdete v tématu [řešení potíží s chybami .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).

## <a name="see-also"></a>Viz také
 [Přehled cílení na více platforem pro Visual Studio](../ide/visual-studio-multi-targeting-overview.md) [.NET Framework pro řešení potíží s více cílemi pro webové projekty](https://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76) , .NET Framework stránku aplikace [s chybami při cílení](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md) na stránku aplikace [Návrháře projektu (C#)](../ide/reference/application-page-project-designer-csharp.md) [, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) [Konfigurace projektů](https://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526) [Postupy: Změna cílové architektury a sady nástrojů platformy](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)
