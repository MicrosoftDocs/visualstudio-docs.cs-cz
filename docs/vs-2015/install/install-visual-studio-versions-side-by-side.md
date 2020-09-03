---
title: Instalace verzí sady Visual Studio vedle sebe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1ef2d51e35a198dbe6da3c1a034dd7c8d1bf8922
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851029"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Souběžná instalace různých verzí sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tuto verzi sady Visual Studio můžete nainstalovat na počítači, ve kterém už je nainstalovaná starší verze. Pokud dojde k chybě instalace, můžete pomocí [Nástroje pro shromažďování protokolů](https://www.microsoft.com/download/details.aspx?id=12493) shromažďovat informace o selháních, abyste mohli problémy ladit sami.

> [!NOTE]
> Doporučujeme nainstalovat [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verze v pořadí, ve kterém byly vydány. Například nainstalujte Visual Studio 2013 před instalací sady Visual Studio 2015.

 Než nainstalujete verze vedle sebe, Projděte si následující podmínky:

- Pokud používáte Visual Studio 2015 k otevření řešení, které bylo vytvořeno v [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] , později můžete znovu otevřít a upravit řešení ve starší verzi, pokud jste neimplementovali žádné funkce, které jsou specifické pro Visual Studio 2015.

- Pokud se pokusíte použít Visual Studio 2015 k otevření řešení, které bylo vytvořeno v [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] nebo dřívější verzi, může být nutné upravit projekty a soubory tak, aby byly kompatibilní se sadou Visual Studio 2015. Další informace najdete na stránce [port, migrace a upgrade projektů sady Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015) .

- Pokud odinstalujete verzi nástroje [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na počítači, ve kterém je nainstalována více než jedna verze, přidružení souborů pro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jsou odebrána pro všechny verze. Tato přidružení souborů můžete přemapovat pomocí tlačítka **obnovit přidružení souborů** na stránce **prostředí**, **Obecné** v dialogovém okně [Možnosti](../ide/reference/general-environment-options-dialog-box.md) .

- Visual Studio neupgraduje automaticky rozšíření, protože ne všechna rozšíření jsou kompatibilní. Rozšíření je nutné přeinstalovat z [Visual Studio Marketplace](https://visualstudiogallery.msdn.microsoft.com/) nebo z vydavatele softwaru.

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework verze a souběžné instalace

- Projekty Visual Basic, Visual C# a Visual F# používají možnost **cílové rozhraní** v **Návrháři projektu** k určení, kterou verzi .NET Framework projekt používá. V případě projektu jazyka C++ lze cílový rámec ručně změnit úpravou souboru. vcxproj. Další informace najdete v tématu [Kompatibilita verzí](https://msdn.microsoft.com/library/2f25e522-456a-48c3-8a53-e5f39275649f).

     Při vytváření projektu můžete určit, která verze .NET Framework projekt cílí v seznamu **.NET Framework** v dialogovém okně **Nový projekt** .

     Informace specifické pro jazyk najdete v příslušném tématu v následující tabulce.

    |Jazyk|Téma|
    |--------------|-----------|
    |[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]|[Stránka Aplikace, návrhář projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)|
    |Visual C#|[Stránka Aplikace, návrhář projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)|
    |Visual F#|[Konfigurace projektů](https://msdn.microsoft.com/library/a1489abb-6294-4f8f-b71f-2cb126393526)|
    |C++|[Postupy: Změna cílové architektury a sady nástrojů platformy](https://msdn.microsoft.com/library/031b1d54-e6e1-4da7-9868-3e75a87d9ffe)|
    |[!INCLUDE[jsprjscript](../includes/jsprjscript-md.md)]|[Spuštění aplikace v jazyce JScript v předchozí verzi modulu CLR (Common Language Runtime)](https://msdn.microsoft.com/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|

## <a name="see-also"></a>Viz také

- [Instalace sady Visual Studio](../install/install-visual-studio-2015.md)
- [Port, migrace a upgrade projektů sady Visual Studio](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects?view=vs-2015)
- [Sestavování izolovaných aplikací C/C++ a souběžných sestavení](https://msdn.microsoft.com/library/9465904e-76f7-48bd-bb3f-c55d8f1699b6)
- [Přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)
