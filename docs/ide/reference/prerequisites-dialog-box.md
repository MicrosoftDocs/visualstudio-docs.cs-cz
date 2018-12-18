---
title: Dialogové okno Požadavky
ms.date: 06/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5faf8e34a9aca77cd6762b5409919fac0978caf7
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2018
ms.locfileid: "39176925"
---
# <a name="prerequisites-dialog-box"></a>dialogové okno Požadavky

**Požadavky** dialogové okno určuje, které nezbytné součásti se instalují, jak jsou nainstalovány a v jakém pořadí jsou balíčky instalovány.

![Dialogové okno požadavky v sadě Visual Studio](media/prerequisites-dialog-box.png)

Pro přístup k dialogovému oknu, vyberte uzel projektu v **Průzkumníka řešení**a pak vyberte **projektu** > **vlastnosti**. Když **Návrháře projektu** se zobrazí, vyberte **publikovat** kartu a potom vyberte **požadavky**. Pro projekty instalace na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. Když **stránky vlastností** dialogové okno se zobrazí, klikněte na tlačítko **požadavky**.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

|Prvek|Popis|
|-------------|-----------------|
|**Vytvořit instalační program pro nainstalování nezbytných součástí**|Zahrne požadované součásti v instalačním programu vaší aplikace (*Setup.exe*) tak, že bude možné nainstalovat před vaše aplikace v pořadí závislosti. Ve výchozím nastavení je tato možnost vybrána. Pokud není vybraná žádná *Setup.exe* se vytvoří.|
|**Vyberte předpoklady k instalaci**|Určuje, jestli se má nainstalovat komponenty, například knihovny modulu runtime rozhraní .NET Framework a jazyka C++.<br /><br />Například výběrem zaškrtávacího políčka vedle položky **SQL Server 2012 Express**, určíte, že instalační program musíte ověřit, zda tato součást je nainstalován v cílovém počítači a nainstalujte ji, pokud není.<br /><br />Podrobné informace o jednotlivých požadovaných balíčcích najdete v tématu [informace o požadavcích](#prerequisites-information).|
|**Stáhnout nezbytné součásti z webu dodavatele součástí**|Určuje, že součásti požadavků mají být nainstalovány z webu dodavatele. Toto je výchozí možnost.|
|**Stáhnout součásti ze stejného umístění, jako je má aplikace**|Určuje, že požadované součásti nainstalovat ze stejného umístění jako aplikace. To zkopíruje všechny požadované balíčky do umístění pro publikování. Tato možnost bude fungovat, pouze pokud jsou balíčky požadovaných součástí ve vývojovém počítači.|
|**Stáhnout nezbytné součásti z následujícího umístění**|Určuje, že požadované součásti nainstalovány z umístění, které zadáte. Můžete použít **Procházet** tlačítko a vyberte umístění.|

## <a name="prerequisites-information"></a>Informace o požadavcích

Požadované součásti, které se zobrazují v **požadavky** dialogové okno se mohou lišit od těch v následujícím seznamu. Požadované balíčky uvedené v **dialogové okno požadavky** se nastaví automaticky při prvním otevření dialogu. Pokud později změníte cílový rámec projektu, budete muset vybrat předpoklady ručně, aby odpovídaly novému cílovému rozhraní.

|Prvek|Popis|
|-------------|-----------------|
|**Rozhraní .NET framework 3.5 SP1**|Tento balíček nainstaluje následující:<br /><br /> – .NET framework verze 2.0, 3.0 a 3.5.<br />-Podpora pro všechny verze rozhraní .NET Framework na 32-bit (x86) a (x64) 64bitové operační systémy.<br />– Jazykové sady pro každou verzi rozhraní .NET Framework je nainstalována spolu s balíčkem.<br />-Service Pack pro rozhraní .NET Framework 2.0 a 3.0.<br /><br /> Rozhraní .NET framework 3.0 je součástí systému Windows Vista a rozhraní .NET Framework 3.5 je součástí sady Visual Studio. Rozhraní .NET framework 3.5 je vyžadováno pro všechny projekty jazyka Visual Basic a C#, které jsou kompilovány pro 32bitové operační systémy a pro který je nastaven cílovou architekturu na **rozhraní .NET Framework 3.5**a pro projekty jazyka Visual Basic a C# zkompilovány pro 64bitové prostředí operační systémy. (IA64 není podporován.) Všimněte si, že jsou projekty Visual Basic a C# zkompilovány pro všechny architektury procesoru ve výchozím nastavení. Další informace najdete v tématu [Visual Studio přehled multiplatformního zacílení](../../ide/visual-studio-multi-targeting-overview.md) a [nasazení nezbytných součástí pro 64bitové aplikace](../../deployment/deploying-prerequisites-for-64-bit-applications.md).|
|**Rozhraní Microsoft .NET Framework 4.x**|Tento balíček nainstaluje rozhraní .NET Framework 4.x x86 a x64 platforem.|
|**Microsoft System CLR Types pro SQL Server 2014 (x64 a x86)**|Tento balíček nainstaluje Microsoft System CLR Types pro SQL Server 2014 x64 nebo x86.|
|**SQL Server 2008 R2 Express**|Tento balíček nainstaluje Microsoft SQL Server 2008 R2 Express, bezplatnou edici systému Microsoft SQL Server 2008 R2, ideální databázi pro malý web, server nebo aplikací klasické pracovní plochy. To je možné zdarma pro vývoj a provoz.|
|**SQL Server 2012 Express**|Tento balíček nainstaluje Microsoft SQL Server 2012 Express.|
|**SQL Server 2012 Express LocalDB**|Tento balíček nainstaluje Microsoft SQL Server 2012 Express LocalDB.|
|**Visual C++ "14" Runtime Libraries (ARM)**|Tento balíček nainstaluje knihovny runtime Visual C++ pro architekturu Itanium, což poskytuje rutiny pro programování pro operační systém Microsoft Windows. Tyto rutiny automatizují mnoho běžných programovacích úloh, které nejsou součástí jazyků C a C++.<br /><br /> Další informace najdete v tématu [C Run-Time Library Reference](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14" Runtime Libraries (x64)**|Tento balíček nainstaluje knihovny běhového modulu Visual C++ pro x64 operační systémy, což poskytuje rutiny pro programování pro operační systém Microsoft Windows. Tyto rutiny automatizují mnoho běžných programovacích úloh, které nejsou součástí jazyků C a C++.<br /><br /> Další informace najdete v tématu [C Run-Time Library Reference](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14" Runtime Libraries (x86)**|Tento balíček nainstaluje knihovny běhového modulu Visual C++ pro x86 operační systémy, což poskytuje rutiny pro programování pro operační systém Microsoft Windows. Tyto rutiny automatizují mnoho běžných programovacích úloh, které nejsou součástí jazyků C a C++.<br /><br /> Další informace najdete v tématu [C Run-Time Library Reference](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Viz také:

- [Stránka Publikovat, Návrhář projektu](../../ide/reference/publish-page-project-designer.md)
- [Nezbytné součásti nasazení aplikace](../../deployment/application-deployment-prerequisites.md)
- [Nasazení nezbytných součástí pro 64bitové aplikace](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Přehled cílení na více verzí sady Visual Studio](../../ide/visual-studio-multi-targeting-overview.md)