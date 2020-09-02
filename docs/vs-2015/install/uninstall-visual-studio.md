---
title: Odinstalace sady Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ed9d33501644c6fa7252dffa758f92c0919653b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546899"
---
# <a name="uninstall-visual-studio"></a>Odinstalace sady Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nejnovější dokumentaci k sadě Visual Studio najdete v tématu [odinstalace sady Visual Studio](/visualstudio/install/uninstall-visual-studio).

Tato stránka vás provede odinstalací sady Visual Studio 2015, starší verze naší integrované sady nástrojů pro zvýšení produktivity pro vývojáře.

## <a name="uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>Odinstalace sady Visual Studio pomocí metody "standardní" Odinstalace

1. V **Ovládacích panelech**na stránce **programy a funkce** zvolte edici produktu, kterou chcete odinstalovat, a pak zvolte **změnit**.

2. V Průvodci instalací klikněte na možnost **odinstalovat**, zvolte možnost **Ano**a postupujte podle pokynů v průvodci.

   Tato verze Standard nebo výchozí metoda zachová některé položky za tím, že vaše první instalace sady Visual Studio byla původně nainstalovaná (například Microsoft .NET Framework, Microsoft Visual C++ distribuovat, Microsoft SQL Server atd.).   Tato nainstalovaná jsou, protože na nich závisí spousta dalších aplikací. Pokud je však chcete také odebrat, vyberte jejich položku v **programech a funkcích**a pak každou z nich odeberte.

## <a name="uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Odinstalace sady Visual Studio a všech dalších souvisejících souborů (tj. pro odinstalaci téměř všeho)

1. Vyhledejte soubor Visual Studio. exe (například vyhledejte "vs_enterprise.exe").

    > [!NOTE]
    > Soubor by měl být v podsložce "%ProgramData%\Package cache", například: C:\ProgramData\Package cache \\ {37e19555-e88d-4aed-9d42-82d0784d2b79} \vs_enterprise.exe

2. Spusťte soubor. exe s použitím parametrů příkazového řádku/Uninstall/Force.

     Například spusťte ```vs_enterprise.exe /uninstall /force``` příkaz, který odebere sadu Visual Studio a většinu základních komponent, které jsou ponechány ve výchozí odinstalaci. Neodebere se ale veškerý další obsah, který můžou nainstalovat doplňky a rozšíření pro Visual Studio (například aktualizace sady Visual Studio a další volitelné komponenty).

    > [!TIP]
    > Alternativně můžete použít nástroj**Celkový odinstalačního**programu k odebrání všeho, co může být nainstalováno v aplikaci Visual Studio nebo aktualizacích sady Visual Studio. To znamená, že všechny verze Visual Studio 2013 nebo novější. Další informace najdete v tématu Nástroj pro [odinstalaci sady Visual Studio](https://github.com/Microsoft/VisualStudioUninstaller/releases) na GitHubu.

## <a name="uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Odinstalace sady Visual Studio v tichém nebo pasivním režimu (tj. Odinstalace ze zdroje)

1. V počítači s nainstalovanou sadou Visual Studio otevřete okno příkazového řádku systému Windows.

2. Zadejte následující parametry:

     *DVDRoot* \\ Instalační soubor<\> \</quiet&#124;/passive> [/norestart]/Uninstall

## <a name="roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Návrat k předchozí verzi nebo vydání sady Visual Studio

1. Odinstalujte sadu Visual Studio pomocí některé z metod uvedených v tomto tématu.

   > [!WARNING]
   > Odinstalace aktuální verze sady Visual Studio (nebo aktualizace sady Visual Studio) a následná instalace předchozí verze nemusí fungovat podle očekávání.
   >
   > Výsledek závisí na tom, kterou verzi nebo verzi sady Visual Studio máte nainstalovanou, které verze jejích komponent jsou nainstalované, které produkty můžou mít závislosti buď k verzi sady Visual Studio, nebo její komponentám, a nakonec na tom, na které verzi sady Visual Studio plánujete instalaci nebo přeinstalaci.  Z důvodu všech těchto proměnných bude standardní odinstalace často opustit komponenty, které nemusí fungovat s předchozími verzemi nebo verzemi sady Visual Studio.
   >
   > Pro dosažení nejlepších výsledků proto doporučujeme použít [Nástroj pro odinstalaci sady Visual Studio](https://github.com/Microsoft/VisualStudioUninstaller/releases).

2. Nainstalujte nebo přeinstalujte starší verzi sady Visual Studio, kterou chcete použít.

   I v případě, že nainstalujete předchozí verzi sady Visual Studio, instalační program se přesto může pokusit použít novější verzi nebo vydání, pokud je k dispozici. Podrobnější informace najdete v tématu [Postupy: instalace konkrétní verze sady Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md) .

## <a name="see-also"></a>Viz také

- [Instalace sady Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)