---
title: Dialogové okno Požadavky
description: Dialogové okno požadavky určuje, které požadované součásti jsou nainstalovány, jak jsou nainstalovány a v jakém pořadí jsou balíčky nainstalovány.
ms.custom: SEO-VS-2020
ms.date: 06/29/2018
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
helpviewer_keywords:
- Prerequisites dialog box
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7384bad2096f98a646487d5d97eed3d387c7de1
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349227"
---
# <a name="prerequisites-dialog-box"></a>dialogové okno Požadavky

Dialogové okno **požadavky** určuje, které požadované součásti jsou nainstalovány, jak jsou nainstalovány a v jakém pořadí jsou balíčky nainstalovány.

![Dialogové okno požadavky v aplikaci Visual Studio](media/prerequisites-dialog-box.png)

Chcete-li získat přístup k dialogovému oknu, vyberte uzel projektu v **Průzkumník řešení** a **Project** pak vyberte  >  **vlastnosti** projektu. Když se zobrazí **Návrhář projektu** , vyberte kartu **publikovat** a pak vyberte **požadované součásti**. Pro projekty instalace klikněte v nabídce **projekt** na příkaz **vlastnosti**. Když se zobrazí dialogové okno **stránky vlastností** , klikněte na **požadavky**.

## <a name="uielement-list"></a>UIElement – seznam

|Element|Popis|
|-------------|-----------------|
|**Vytvoření instalačního programu pro instalaci požadovaných součástí**|Zahrnuje požadované součásti v instalačním programu aplikace ( *Setup.exe* ) tak, aby byly nainstalovány před vaší aplikací v závislosti na závislosti. Tato možnost je vybrána ve výchozím nastavení. Pokud není vybráno, není vytvořena žádná *Setup.exe* .|
|**Vyberte požadavky pro instalaci.**|Určuje, jestli se mají nainstalovat komponenty, jako jsou .NET Framework a běhové knihovny C++.<br /><br />Například zaškrtnutím políčka vedle **SQL Server 2012 Express** zadáte, že instalační program musí ověřit, zda je tato součást nainstalována na cílovém počítači, a nainstalovat ji, pokud není.<br /><br />Podrobné informace o každém balíčku předpokladů najdete v tématu [informace o požadavcích](#prerequisites-information).|
|**Stáhnout požadavky z webu dodavatele součásti**|Určuje, že požadované součásti budou nainstalovány z webu dodavatele. Toto je výchozí možnost.|
|**Stáhnout požadavky ze stejného umístění jako moje aplikace**|Určuje, že požadované součásti budou nainstalovány ze stejného umístění jako aplikace. Tím se zkopírují všechny požadované balíčky do umístění pro publikování. Tato možnost bude fungovat, pouze pokud jsou balíčky požadovaných součástí ve vývojovém počítači.|
|**Stáhnout požadované součásti z následujícího umístění**|Určuje, že požadované součásti budou nainstalovány z umístění, které zadáte. Můžete použít tlačítko **Procházet** a vybrat umístění.|

> [!NOTE]
> Informace o tom, kam umístit požadavky, najdete v tématu [Vytvoření balíčků zaváděcího nástroje](../../deployment/creating-bootstrapper-packages.md#create-custom-bootstrapper-packages).

## <a name="prerequisites-information"></a>Informace o požadavcích

Požadované součásti, které se zobrazí v dialogovém okně **předpoklady** , se mohou lišit od těch, které jsou uvedeny v následujícím seznamu. Požadované balíčky uvedené v **dialogovém okně požadavky** se nastaví automaticky při prvním otevření dialogového okna. Pokud následně změníte cílovou architekturu projektu, je nutné vybrat požadované součásti ručně, aby odpovídaly novému cílovému rozhraní.

|Element|Popis|
|-------------|-----------------|
|**.NET Framework 3.5 SP1**|Tento balíček nainstaluje následující:<br /><br /> -.NET Framework verze 2,0, 3,0 a 3,5.<br />-Podpora pro všechny verze .NET Framework v operačních systémech 32 (x86) a 64-bit (x64).<br />-Jazykové sady pro každou verzi .NET Framework, která se instaluje s balíčkem.<br />– Aktualizace Service Pack pro .NET Framework 2,0 a 3,0.<br /><br /> .NET Framework 3,0 je součástí systému Windows Vista a součástí sady Visual Studio je .NET Framework 3,5. .NET Framework 3,5 je vyžadován pro všechny projekty Visual Basic a C#, které jsou kompilovány pro 32 operační systémy a pro které je cílové rozhraní nastaveno na **.NET Framework 3,5** a pro Visual Basic a C# projekty zkompilované pro operační systémy s 64. (IA64 není podporováno.) Všimněte si, že projekty Visual Basic a C# jsou ve výchozím nastavení kompilovány pro všechny architektury procesoru. Další informace najdete v tématu věnovaném [přehledu cílení na rozhraní](../../ide/visual-studio-multi-targeting-overview.md) a [nasazení požadavků pro 64 – bitové aplikace](../../deployment/deploying-prerequisites-for-64-bit-applications.md).|
|**Microsoft .NET Framework 4. x**|Tento balíček nainstaluje .NET Framework 4. x pro platformy x86 i x64.|
|**Microsoft System CLR types pro SQL Server 2014 (x64 a x86)**|Tento balíček nainstaluje typy CLR systému Microsoft pro SQL Server 2014 pro x64 nebo x86.|
|**SQL Server 2008 R2 Express**|Tento balíček nainstaluje Microsoft SQL Server 2008 R2 Express, bezplatnou edici Microsoft SQL Server 2008 R2, ideální databází pro malé webové, serverové nebo desktopové aplikace. Dá se použít zdarma pro vývoj a produkci.|
|**SQL Server 2012 Express**|Tento balíček nainstaluje Microsoft SQL Server 2012 Express.|
|**SQL Server 2012 Express LocalDB**|Tento balíček nainstaluje Microsoft SQL Server 2012 Express LocalDB.|
|**Visual C++ "14" běhové knihovny (ARM)**|Tento balíček nainstaluje Visual C++ knihovny runtime pro architekturu Itanium, která poskytuje rutiny pro programování pro operační systém Microsoft Windows. Tyto rutiny automatizují mnoho běžných programovacích úloh, které nejsou poskytovány jazyky C a C++.<br /><br /> Další informace najdete v tématu [Referenční dokumentace knihovny C Run-Time](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14" běhové knihovny (x64)**|Tento balíček nainstaluje Visual C++ knihovny runtime pro operační systémy x64, které poskytují rutiny pro programování pro operační systém Microsoft Windows. Tyto rutiny automatizují mnoho běžných programovacích úloh, které nejsou poskytovány jazyky C a C++.<br /><br /> Další informace najdete v tématu [Referenční dokumentace knihovny C Run-Time](/cpp/c-runtime-library/c-run-time-library-reference).|
|**Visual C++ "14" běhové knihovny (x86)**|Tento balíček nainstaluje Visual C++ knihovny runtime pro operační systémy x86, které poskytují rutiny pro programování pro operační systém Microsoft Windows. Tyto rutiny automatizují mnoho běžných programovacích úloh, které nejsou poskytovány jazyky C a C++.<br /><br /> Další informace najdete v tématu [Referenční dokumentace knihovny C Run-Time](/cpp/c-runtime-library/c-run-time-library-reference).|

## <a name="see-also"></a>Viz také

- [Publikovat stránku, návrhář projektu](../../ide/reference/publish-page-project-designer.md)
- [Požadavky nasazení aplikace](../../deployment/application-deployment-prerequisites.md)
- [Nasazení nezbytných součástí pro 64bitové aplikace](../../deployment/deploying-prerequisites-for-64-bit-applications.md)
- [Přehled cílení na rozhraní](../../ide/visual-studio-multi-targeting-overview.md)
