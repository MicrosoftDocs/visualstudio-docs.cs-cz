---
title: Dialogové okno Požadavky
ms.date: 06/29/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ecbba1a1c5e8670fd9adcafdfed8cec21dd3912
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567902"
---
# <a name="prerequisites-dialog-box"></a>dialogové okno Požadavky

Dialogové okno **Požadavky** určuje, které součásti jsou nainstalovány, jak jsou nainstalovány a jaké jsou balíčky nainstalovány.

![Dialogové okno Požadavky v sadě Visual Studio](media/prerequisites-dialog-box.png)

Chcete-li získat přístup k dialogovému oknu, vyberte uzel projektu v **Průzkumníku řešení**a pak vyberte**Vlastnosti** **projektu** > . Po zobrazení **Návrháře projektů** vyberte kartu **Publikovat** a pak vyberte **Požadavky**. V případě instalačních projektů klepněte v nabídce **Projekt** na **položku Vlastnosti**. Po zobrazení dialogového okna **Stránky vlastností** klepněte na **položku Požadavky**.

## <a name="uielement-list"></a>Seznam Prvků UI

|Element|Popis|
|-------------|-----------------|
|**Vytvoření instalačního programu pro instalaci nezbytných součástí**|Zahrne požadované součásti do instalačního programu aplikace *(Setup.exe),* aby byly nainstalovány před aplikací v pořadí závislosti. Tato možnost je vybrána ve výchozím nastavení. Pokud není vybrána, není vytvořen žádný *program Setup.exe.*|
|**Zvolte, které požadavky chcete nainstalovat**|Určuje, zda mají být nainstalovány součásti, jako jsou například knihovny rozhraní .NET Framework a C++ runtime.<br /><br />Zaškrtnutím políčka vedle serveru **SQL Server 2012 Express**například určíte, že instalační program musí ověřit, zda je tato součást nainstalována v cílovém počítači, a nainstalovat ji, pokud není.<br /><br />Podrobné informace o jednotlivých nezbytných balíčcích naleznete v [tématu Požadavky informace](#prerequisites-information).|
|**Stáhnout požadavky z webu dodavatele komponenty**|Určuje, že požadované součásti budou nainstalovány z webu dodavatele. Toto je výchozí možnost.|
|**Stáhnout požadavky ze stejného umístění jako moje aplikace**|Určuje, že požadované součásti budou nainstalovány ze stejného umístění jako aplikace. Tím se zkopírují všechny požadované balíčky do umístění publikování. Tato možnost bude fungovat, pouze pokud jsou balíčky požadovaných součástí ve vývojovém počítači.|
|**Stáhnout požadavky z následujícího umístění**|Určuje, že požadované součásti budou nainstalovány z umístění, které zadáte. Umístění můžete vybrat pomocí tlačítka **Procházet.**|

> [!NOTE]
> Informace o tom, kam umístit požadavky, naleznete v [tématu Vytvoření balíčků zaváděcího nástroje](../../deployment/creating-bootstrapper-packages.md#create-custom-bootstrapper-packages).

## <a name="prerequisites-information"></a>Informace o požadavcích

Předpokladové součásti, které se zobrazí v dialogovém okně **Požadavky,** se mohou lišit od součástí v následujícím seznamu. Balíčky požadavků uvedené v **dialogovém okně Požadavky** jsou nastaveny automaticky při prvním otevření dialogového okna. Pokud následně změníte cílové rozhraní projektu, budete muset vybrat požadavky ručně tak, aby odpovídaly nové cílové rozhraní.

|Element|Popis|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|Tento balíček nainstaluje následující:<br /><br /> - Rozhraní .NET Framework verze 2.0, 3.0 a 3.5.<br />- Podpora pro všechny verze rozhraní .NET Framework na 32bitových (x86) a 64bitových (x64) operačních systémech.<br />- Jazykové sady pro každou verzi rozhraní .NET Framework, která je nainstalována s balíčkem.<br />- Aktualizace Service Pack pro rozhraní .NET Framework 2.0 a 3.0.<br /><br /> Rozhraní .NET Framework 3.0 je součástí systému Windows Vista a rozhraní .NET Framework 3.5 je součástí sady Visual Studio. Rozhraní .NET Framework 3.5 je vyžadováno pro všechny projekty jazyka Visual Basic a C#, které jsou kompilovány pro 32bitové operační systémy a pro které je cílová architektura nastavena na **rozhraní .NET Framework 3.5**a pro projekty jazyka Visual Basic a C# zkompilované pro 64bitové operační systémy. (IA64 není podporován.) Všimněte si, že visual basic a C# projekty jsou kompilovány pro všechny architektury procesoru ve výchozím nastavení. Další informace najdete v [tématu Přehled cílení v rámci](../../ide/visual-studio-multi-targeting-overview.md) a Nasazení požadavků pro [64bitové aplikace](../../deployment/deploying-prerequisites-for-64-bit-applications.md).|
|**Rozhraní Microsoft .NET Framework 4.x**|Tento balíček nainstaluje rozhraní .NET Framework 4.x pro platformy x86 i x64.|
|**Typy CLR systému Microsoft pro SQL Server 2014 (x64 a x86)**|Tento balíček nainstaluje typy CLR systému Microsoft pro SQL Server 2014 pro x64 nebo x86.|
|**SQL Server 2008 R2 Express**|Tento balíček nainstaluje Microsoft SQL Server 2008 R2 Express, bezplatnou edici microsoft sql serveru 2008 R2, ideální databáze pro malé webové, serverové nebo desktopové aplikace. Může být použit zdarma pro vývoj a výrobu.|
|**SQL Server 2012 Express**|Tento balíček nainstaluje Microsoft SQL Server 2012 Express.|
|**SQL Server 2012 Express LocalDB**|Tento balíček nainstaluje Microsoft SQL Server 2012 Express LocalDB.|
|**Visual C++ "14" Runtime knihovny (ARM)**|Tento balíček nainstaluje knihovny Visual C++ run-time pro architekturu Itanium, které poskytují rutiny pro programování operačního systému Microsoft Windows. Tyto rutiny automatizují mnoho běžných programovacích úloh, které nejsou poskytovány jazyky C a C++.<br /><br /> Další informace naleznete v tématu [C Run-Time Library Reference](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14" Runtime knihovny (x64)**|Tento balíček nainstaluje knihovny visual c++ run-time pro operační systémy x64, které poskytují rutiny pro programování operačního systému Microsoft Windows. Tyto rutiny automatizují mnoho běžných programovacích úloh, které nejsou poskytovány jazyky C a C++.<br /><br /> Další informace naleznete v tématu [C Run-Time Library Reference](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14" Runtime knihovny (x86)**|Tento balíček nainstaluje knihovny visual c++ run-time pro operační systémy x86, které poskytují rutiny pro programování operačního systému Microsoft Windows. Tyto rutiny automatizují mnoho běžných programovacích úloh, které nejsou poskytovány jazyky C a C++.<br /><br /> Další informace naleznete v tématu [C Run-Time Library Reference](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Viz také

- [Publikovat stránku, návrhář projektu](../../ide/reference/publish-page-project-designer.md)
- [Požadavky na nasazení aplikace](../../deployment/application-deployment-prerequisites.md)
- [Nasazení nezbytných součástí pro 64bitové aplikace](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Přehled cílení na rozhraní](../../ide/visual-studio-multi-targeting-overview.md)
