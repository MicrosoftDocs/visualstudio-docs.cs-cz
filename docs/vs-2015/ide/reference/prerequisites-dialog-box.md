---
title: Dialogové okno požadavky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.BaseProvider.Dialog.Bootstrapper
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Prerequisites dialog box
ms.assetid: 53ac863c-77a0-409b-91e5-7a4bd8b8474e
caps.latest.revision: 79
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6aff33e7129123e2f910116a5d9352944e1c064a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49183947"
---
# <a name="prerequisites-dialog-box"></a>Dialogové okno Požadavky
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Toto dialogové okno určuje, které nezbytné součásti se instalují, jak jsou nainstalovány a v jakém pořadí jsou nainstalované balíčky.  
  
 Pro přístup k tomuto dialogovému oknu, vyberte uzel projektu v **Průzkumníka řešení**a potom na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. Když **Návrháře projektu** se zobrazí, klikněte na tlačítko **publikovat** kartu. Na **publikovat** klikněte na **požadavky**. Pro projekty instalace na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. Když **stránky vlastností** dialogové okno se zobrazí, klikněte na tlačítko **požadavky**.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
  
|Prvek|Popis|  
|-------------|-----------------|  
|**Vytvořit instalační program pro nainstalování nezbytných součástí**|Zahrne požadované součásti v instalačním programu vaší aplikace (Setup.exe) tak, aby se nainstalují ještě před aplikací, v pořadí závislosti. Ve výchozím nastavení je tato možnost vybrána. Pokud není zaškrtnuto, nevytvoří se Setup.exe.|  
|**Vyberte předpoklady k instalaci**|Určuje, jestli se má nainstalovat komponenty, jako je [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], Crystal Reports atd.<br /><br /> Například výběrem zaškrtávacího políčka vedle položky **SQL Server 2005 Express Edition SP2**, určíte, že instalačního programu ověřte, zda tato součást je nainstalován v cílovém počítači a nainstalujte ji, pokud ještě není nainstalovaná.<br /><br /> Podrobné informace o jednotlivých požadovaných balíčcích viz tabulku informace o požadavcích dále v tomto tématu.|  
|**Zkontrolovat službu Microsoft Update pro další distribuovatelné součásti**|Kliknutím na tento odkaz vás přesměruje na [balíčky zaváděcího nástroje Redistribuce součástí](http://go.microsoft.com/fwlink/?LinkId=208835) webu kontrolu aktualizací.|  
|**Stáhnout nezbytné součásti z webu dodavatele součástí**|Určuje, že součásti požadavků mají být nainstalovány z webu dodavatele. Toto je výchozí možnost.|  
|**Stáhnout součásti ze stejného umístění, jako je má aplikace**|Určuje, že požadované součásti nainstalovat ze stejného umístění jako aplikace. To zkopíruje všechny požadované balíčky do umístění pro publikování. Tato možnost bude fungovat, pouze pokud jsou balíčky požadovaných součástí ve vývojovém počítači.|  
|**Stáhnout nezbytné součásti z následujícího umístění**|Určuje, že požadované součásti nainstalovány z umístění, které jste vybrali. Můžete použít **Procházet** tlačítko a vyberte umístění.|  
  
## <a name="prerequisites-information"></a>Informace o požadavcích  
 Požadované součásti, které se zobrazují v **požadavky** dialogové okno se mohou lišit od těch v následujícím seznamu. Požadované balíčky uvedené v **dialogové okno požadavky** se nastaví automaticky při prvním otevření dialogu. Pokud později změníte cílový rámec projektu, budete muset vybrat předpoklady ručně, aby odpovídaly novému cílovému rozhraní.  
  
|Prvek|Popis|  
|-------------|-----------------|  
|**Rozhraní .NET framework 3.5 SP1**|Tento balíček nainstaluje následující:<br /><br /> – .NET framework verze 2.0, 3.0 a 3.5.<br />-Podpora pro všechny verze rozhraní .NET Framework na 32-bit (x86) a (x64) 64bitové operační systémy.<br />– Jazykové sady pro každou verzi rozhraní .NET Framework je nainstalována spolu s balíčkem.<br />-Service Pack pro rozhraní .NET Framework 2.0 a 3.0.<br /><br /> Rozhraní .NET framework 3.0 je součástí systému Windows Vista a rozhraní .NET Framework 3.5 je součástí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Rozhraní .NET framework 3.5 je vyžadováno pro všechny jazyka Visual Basic a Visual C# projekty, které jsou kompilovány pro 32bitové operační systémy a pro který je nastaven cílovou architekturu na **rozhraní .NET Framework 3.5**a pro projekty jazyka Visual Basic a Visual C# zkompilovány pro 64bitové operační systémy. (IA64 není podporován.) Všimněte si, že jsou projekty Visual Basic a Visual C# zkompilovány pro všechny architektury procesoru ve výchozím nastavení. Další informace najdete v tématu [Visual Studio přehled multiplatformního zacílení](../../ide/visual-studio-multi-targeting-overview.md), [redistribuci rozhraní .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287), a [nasazení nezbytných součástí pro 64bitové aplikace](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Ve výchozím nastavení je vybraná tato položka.|  
|**Profil klienta rozhraní .NET framework 3.5 SP1**|Rozhraní .NET Framework Client Profile je podmnožinou úplné rozhraní .NET Framework 3.5 SP1, zaměřuje na klientské aplikace. Poskytuje zjednodušenou podmnožinu Windows Presentation Foundation (WPF), Windows Forms, Windows Communication Foundation (WCF) a ClickOnce funkce. To umožňuje scénáře rychlého nasazení WPF, Windows Forms, WCF a konzolových aplikací využívajících rozhraní .NET Framework Client Profile. Další informace najdete v tématu [rozhraní .NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).|  
|**Microsoft .NET Framework 4 (x86 a x64)**|Tento balíček nainstaluje rozhraní .NET Framework 4 pro platformy x86 a x64.<br /><br /> Další informace najdete v tématu [Visual Studio přehled multiplatformního zacílení](../../ide/visual-studio-multi-targeting-overview.md), [redistribuci rozhraní .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287), a [nasazení nezbytných součástí pro 64bitové aplikace](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Ve výchozím nastavení je vybraná tato položka.|  
|**Microsoft .NET Framework 4 Client Profile (x86 a x64)**|Rozhraní .NET Framework 4 Client Profile je podmnožinou úplné rozhraní .NET Framework 4, zaměřuje na klientské aplikace. Poskytuje zjednodušenou podmnožinu Windows Presentation Foundation (WPF), Windows Forms, Windows Communication Foundation (WCF) a ClickOnce funkce. To umožňuje scénáře rychlého nasazení WPF, Windows Forms a konzolové aplikace, které se zaměřují rozhraní .NET Framework 4 Client Profile. Další informace najdete v tématu [rozhraní .NET Framework Client Profile](http://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).|  
|**Microsoft Office 2007 primární spolupracující sestavení**|Tento balíček nainstaluje Primary Interop Assemblies 2007 produkty Microsoft Office. Primární spolupracující sestavení umožňuje spravovanému kódu pracovat s aplikací sady Microsoft Office založené na modelu COM. objektovém modelu. Další informace najdete v tématu [sestavení primární spolupráce Office](http://msdn.microsoft.com/library/aa29d12c-185f-4558-a7cd-3d85f924203d).|  
|**Sady Microsoft Visual Basic PowerPack verze 10.0**|Power Pack jsou doplňky, ovládací prvky, komponenty a nástroje pro pomoc při vývoji aplikací jazyka Visual Basic. Tato verze obsahuje <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> komponenta, která umožňuje vytisknout obsah formuláře Windows a knihovny kompatibility tiskárny, což umožňuje spuštění bez úprav kódu tiskárny jazyka Visual Basic 6.0.|  
|**Microsoft Visual F # Runtime pro .NET 2.0**|Tento balíček nainstaluje knihovny běhového modulu Visual F # pro x86 a x64 operační systémy, což poskytuje podporu pro funkční programování, jakož i tradiční (procedurální) objektově orientované a imperativní programování. Tento balíček musí být nainstalován, pokud aplikace nebo její součásti jsou vytvořeny v jazyce Visual F # a rozhraní .NET Framework 2.0, .NET Framework 3.0 nebo .NET Framework 3.5.<br /><br /> Další informace najdete v tématu [referenční dokumentace jazyka F #](http://msdn.microsoft.com/library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|  
|**Microsoft Visual F # Runtime pro rozhraní .NET 4.0**|Tento balíček nainstaluje knihovny běhového modulu Visual F # pro x86 a x64 operační systémy, což poskytuje podporu pro funkční programování, jakož i tradiční (procedurální) objektově orientované a imperativní programování. Tento balíček musí být nainstalován, pokud aplikace nebo její součásti jsou vytvořeny v jazyce Visual F # a rozhraní .NET Framework 4.<br /><br /> Další informace najdete v tématu [referenční dokumentace jazyka F #](http://msdn.microsoft.com/library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|  
|**Prohlížeč sestav aplikace Microsoft Visual Studio 2010**|Tento balíček nainstaluje ovládací prvky prohlížeče sestav, které slouží k přidání bohatého vykazování dat do formulářů Windows a aplikací ASP.NET.|  
|**Microsoft Visual Studio 2010 pro Office Runtime (x86 a x64)**|Nástroje Office developer tools v sadě Visual Studio nabízí snadno použitelné a integrované nástroje pro vytváření přizpůsobených obchodních řešení sady Microsoft Office. Můžete vytvářet spravovaná, inteligentní klientská řešení využívající aplikace systému Office jako uživatelské rozhraní. Nástroje vývojářům umožňují vytvářet bezpečná řešení, která se dají snadno nasadit a udržovat.<br /><br /> Další informace najdete v tématu [postupy: publikování aplikací ClickOnce pomocí řešení pro Office](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).|  
|**SQL Server 2005 Express Edition SP2 (x 86)**|Tento balíček nainstaluje Microsoft SQL Server 2005 Express Edition SP2, databázovou aplikaci, která je založena na [!INCLUDE[sqprsqext](../../includes/sqprsqext-md.md)]. SQL Server Express je náhradou pro Microsoft SQL Server Desktop Engine (MSDE). SQL Server Express je zdarma a můžete znovu distribuovat (podle dohody) a funguje jako klientská databáze i základní serverová databáze. Je stejný jako SQL Server 2005, vyjma následujících rozdílů:<br /><br /> – Bez podpory funkcí organizace.<br />– Omezeno na jeden procesor.<br />– limit paměti 1 gigabajt (GB) pro fond vyrovnávací paměti.<br />-Maximální velikost 4 GB pro databáze.|  
|**SQL Server 2008 Express**|Tento balíček nainstaluje Microsoft SQL Server 2008 Express, bezplatnou edici systému Microsoft SQL Server 2008, ideální databázi pro malý web, server nebo aplikací klasické pracovní plochy. To je možné zdarma pro vývoj a provoz. Bezplatné [registrace](http://go.microsoft.com/fwlink/?LinkId=130380) , je třeba distribuce SQL Server 2008 Express s aplikací.<br /><br /> Chování zaváděcího nástroje je následující:<br /><br /> – Pokud má počítač již systému SQL Server 2008 Express nebo novější, zůstane počítač na serveru SQL Server 2008 Express nebo novější.<br />– Pokud počítač nemá libovolnou verzi systému SQL Server 2008 Express nebo novější, balíček nainstaluje nejnovější verzi SQL Server 2008 Express SP1.<br /><br /> Další informace o systému SQL Server 2008 Express, navštivte [ http://go.microsoft.com/fwlink/?LinkId=183586 ](http://go.microsoft.com/fwlink/?LinkId=183586).|  
|**Knihovny Visual C++ 2010 Runtime (IA64)**|Tento balíček nainstaluje knihovny runtime Visual C++ pro architekturu Itanium, což poskytuje rutiny pro programování pro operační systém Microsoft Windows. Tyto rutiny automatizují mnoho běžných programovacích úloh, které nejsou součástí jazyků C a C++.<br /><br /> Další informace najdete v tématu [C Run-Time Library Reference](http://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|  
|**Knihovny Visual C++ 2010 Runtime (x64)**|Tento balíček nainstaluje knihovny běhového modulu Visual C++ pro x64 operační systémy, což poskytuje rutiny pro programování pro operační systém Microsoft Windows. Tyto rutiny automatizují mnoho běžných programovacích úloh, které nejsou součástí jazyků C a C++.<br /><br /> Další informace najdete v tématu [C Run-Time Library Reference](http://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|  
|**Knihovny Visual C++ 2010 Runtime (x86)**|Tento balíček nainstaluje knihovny běhového modulu Visual C++ pro x86 operační systémy, což poskytuje rutiny pro programování pro operační systém Microsoft Windows. Tyto rutiny automatizují mnoho běžných programovacích úloh, které nejsou součástí jazyků C a C++.<br /><br /> Další informace najdete v tématu [C Run-Time Library Reference](http://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|  
|**Instalační služba systému Windows 3.1**|Tento balíček nainstaluje instalační služby systému Microsoft Windows redistributable, verze 3.1, což umožňuje instalaci instalačních projektů instalace Instalační služby systému Windows. Je předinstalován v systému Windows Server 2003 s aktualizací SP1 a novější.<br /><br /> Ve výchozím nastavení je vybraná tato položka.|  
|**Windows Installer 4.5**|Tento balíček nainstaluje instalační služby systému Microsoft Windows redistributable, verze 4.5, což umožňuje instalaci instalačních projektů instalace Instalační služby systému Windows.|  
  
## <a name="see-also"></a>Viz také  
 [Publikovat stranu, Návrhář projektu](../../ide/reference/publish-page-project-designer.md)   
 [Nezbytné součásti nasazení aplikace](../../deployment/application-deployment-prerequisites.md)   
 [Redistribuce rozhraní .NET Framework](http://msdn.microsoft.com/en-us/a18d0456-fd89-493e-97f4-756505bfe287)   
 [Nasazení nezbytných součástí pro 64bitové aplikace](../../deployment/deploying-prerequisites-for-64-bit-applications.md)   
 [Přehled cílení na více verzí sady Visual Studio](../../ide/visual-studio-multi-targeting-overview.md)



