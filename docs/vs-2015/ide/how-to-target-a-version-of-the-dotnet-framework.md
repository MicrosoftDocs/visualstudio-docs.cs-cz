---
title: 'Postupy: cílení na určitou verzi rozhraní .NET Framework | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], targeting .NET Framework version
ms.assetid: dea62d25-3d1b-492e-a6cc-b5154489800a
caps.latest.revision: 53
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3370c62535f2bb915115533ea79f4b913c3ac347
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182361"
---
# <a name="how-to-target-a-version-of-the-net-framework"></a>Postupy: Cílení na verzi rozhraní .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tento dokument popisuje, jak při vytvoření projektu cílit na určitou verzi rozhraní .NET Framework a jak změnit cílenou verzi v existujícím projektu v jazyce Visual Basic, Visual C# nebo Visual F#.  
  
> [!IMPORTANT]
>  Informace o tom, jak změnit cílovou verzi pro projekty C++, naleznete v tématu [postupy: Změna cílové architektury a sady nástrojů](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).  
  
 **V tomto tématu**  
  
-   [Cílení na určitou verzi při vytváření projektu](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_new)  
  
-   [Změna cílové verze](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing)  
  
##  <a name="bkmk_new"></a> Cílení na určitou verzi při vytváření projektu  
 Šablony, které můžete použít při vytváření projektu, jsou určeny verzí rozhraní .NET Framework, na kterou cílíte.  
  
> [!NOTE]
>  V edicích Express sady Visual Studio, je nutné nejprve vytvořit projekt a pak můžete změnit cíl, jako [Změna cílové verze](../ide/how-to-target-a-version-of-the-dotnet-framework.md#bkmk_existing) popisuje dál v tomto tématu.  
  
#### <a name="to-target-a-version-when-you-create-a-project"></a>Cílení na určitou verzi při vytváření projektu  
  
1.  V panelu nabídky zvolte **souboru**, **nový**, **projektu**.  
  
2.  V seznamu v horní části **nový projekt** dialogovém okně zvolte verzi rozhraní .NET Framework, který má váš projekt zaměřit.  
  
    > [!NOTE]
    >  Se sadou Visual Studio se obvykle instaluje jen jedna verze rozhraní .NET Framework. Pokud chcete cílit na jinou verzi, je nejprve třeba zkontrolovat, zda je nainstalovaná. Zobrazit [cílení na více verzí sady Visual Studio přehled](../ide/visual-studio-multi-targeting-overview.md).  
  
3.  V seznamu nainstalovaných šablon zvolte typ projektu, který chcete vytvořit, pojmenujte projekt a klikněte na tlačítko **OK** tlačítko.  
  
     V seznamu šablon jsou uvedeny pouze projekty, které jsou podporovány vámi vybranou verzí rozhraní .NET Framework.  
  
##  <a name="bkmk_existing"></a> Změna cílové verze  
 Pomocí tohoto postupu můžete změnit cílovou verzi rozhraní .NET Framework v projektu jazyka Visual Basic, Visual C# nebo Visual F #.  
  
#### <a name="to-change-the-targeted-version"></a>Změna cílené verze  
  
1.  V **Průzkumníka řešení**, otevřete místní nabídku pro projekt, který chcete změnit a klikněte na tlačítko **vlastnosti**.  
  
     ![Visual Studio Solution Explorer Properties](../ide/media/vs-slnexplorer-properties.png "vs_slnExplorer_Properties")  
  
    > [!IMPORTANT]
    >  Informace o tom, jak změnit cílovou verzi pro projekty C++, naleznete v tématu [postupy: Změna cílové architektury a sady nástrojů](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe).  
  
2.  V levém sloupci okna vlastností zvolte **aplikace** kartu.  
  
     ![Visual Studio aplikaci vlastnosti karty](../ide/media/vs-slnexplorer-properties-applicationtab.png "vs_slnExplorer_Properties_ApplicationTab")  
  
    > [!NOTE]
    >  Po vytvoření aplikace Windows Store nelze změnit cílenou verzi systému Windows nebo .NET Framework.  
  
3.  V **Cílová architektura** , zvolte verzi, která chcete.  
  
4.  V dialogovém okně ověřování, který se zobrazí, zvolte **Ano** tlačítko.  
  
     Projekt se uvolní. Až se znovu načte, bude cílit na verzi rozhraní .NET Framework, kterou jste vybrali.  
  
    > [!NOTE]
    >  Pokud váš kód obsahuje odkazy na jinou verzi rozhraní .NET Framework, než na kterou cílíte, mohou se při kompilaci či spuštění kódu zobrazit chybové zprávy. Chcete-li tyto chyby vyřešit, je třeba upravit odkazy. Zobrazit [řešení potíží s cílením na rozhraní .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md).  
  
## <a name="see-also"></a>Viz také  
 [Cílení na více verzí sady Visual Studio – přehled](../ide/visual-studio-multi-targeting-overview.md)   
 [Rozhraní .NET framework Multi-Targeting pro webové projekty ASP.NET](http://msdn.microsoft.com/library/8b8145a9-62f6-4fc4-8a83-47b0487cbe76)   
 [Řešení potíží s cílením na rozhraní .NET Framework](../msbuild/troubleshooting-dotnet-framework-targeting-errors.md)   
 [Stránka aplikace, Návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Stránka aplikace, Návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)   
 [Konfigurace projektů](http://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)   
 [Postupy: Změna cílové architektury a sady nástrojů](http://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)



