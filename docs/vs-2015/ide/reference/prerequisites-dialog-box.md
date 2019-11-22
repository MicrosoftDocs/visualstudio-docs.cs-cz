---
title: Dialogové okno požadavky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b8e5e004d2e337900d88f72d92bfd439103b87e0
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297838"
---
# <a name="prerequisites-dialog-box"></a>Dialogové okno Požadavky
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Toto dialogové okno určuje, které požadované součásti jsou nainstalovány, jak jsou nainstalovány a v jakém pořadí jsou balíčky nainstalovány.

 Chcete-li získat přístup k tomuto dialogovému oknu, vyberte uzel projektu v **Průzkumník řešení**a potom v nabídce **projekt** klikněte na příkaz **vlastnosti**. Když se zobrazí **Návrhář projektu** , klikněte na kartu **publikovat** . Na stránce **publikovat** klikněte na **požadované součásti**. Pro projekty instalace klikněte v nabídce **projekt** na příkaz **vlastnosti**. Když se zobrazí dialogové okno **stránky vlastností** , klikněte na **požadavky**.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

|Prvek|Popis|
|-------------|-----------------|
|**Vytvoření instalačního programu pro instalaci požadovaných součástí**|Zahrnuje požadované součásti v instalačním programu aplikace (Setup. exe), aby byly nainstalovány před aplikací v závislosti na závislosti. Ve výchozím nastavení je tato možnost vybraná. Pokud není vybrána, není vytvořen soubor Setup. exe.|
|**Vyberte požadavky pro instalaci.**|Určuje, jestli se mají nainstalovat komponenty, jako jsou [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], Crystal Reports a tak dále.<br /><br /> Například zaškrtnutím políčka vedle **SQL Server 2005 Express Edition SP2**určíte, že instalační program ověří, jestli je tato součást nainstalovaná na cílovém počítači, a nainstalujte ji, pokud ještě není nainstalovaná.<br /><br /> Podrobné informace o jednotlivých požadovaných balíčcích najdete v tabulce s informacemi o požadovaných součástech dále v tomto tématu.|
|**Kontrolovat Microsoft Update pro další distribuovatelné součásti**|Kliknutím na tento odkaz přejdete na web [balíčky zaváděcího nástroje pro redistribuci součástí](https://go.microsoft.com/fwlink/?LinkId=208835) , kde najdete aktualizace.|
|**Stáhnout požadavky z webu dodavatele součásti**|Určuje, že požadované součásti budou nainstalovány z webu dodavatele. Toto je výchozí možnost.|
|**Stáhnout požadavky ze stejného umístění jako moje aplikace**|Určuje, že požadované součásti budou nainstalovány ze stejného umístění jako aplikace. Tím se zkopírují všechny požadované balíčky do umístění pro publikování. Tato možnost bude fungovat, pouze pokud jsou balíčky požadovaných součástí ve vývojovém počítači.|
|**Stáhnout požadované součásti z následujícího umístění**|Určuje, že požadované součásti budou nainstalovány z umístění, které jste vybrali. Můžete použít tlačítko **Procházet** a vybrat umístění.|

## <a name="prerequisites-information"></a>Informace o požadavcích
 Požadované součásti, které se zobrazí v dialogovém okně **předpoklady** , se mohou lišit od těch, které jsou uvedeny v následujícím seznamu. Požadované balíčky uvedené v **dialogovém okně požadavky** se nastaví automaticky při prvním otevření dialogového okna. Pokud následně změníte cílovou architekturu projektu, bude nutné vybrat požadované součásti ručně, aby odpovídaly novému cílovému rozhraní.

|Prvek|Popis|
|-------------|-----------------|
|**.NET Framework 3,5 SP1**|Tento balíček nainstaluje následující:<br /><br /> -.NET Framework verze 2,0, 3,0 a 3,5.<br />-Podpora pro všechny verze .NET Framework v operačních systémech 32 (x86) a 64-bit (x64).<br />-Jazykové sady pro každou verzi .NET Framework, která se instaluje s balíčkem.<br />– Aktualizace Service Pack pro .NET Framework 2,0 a 3,0.<br /><br /> .NET Framework 3,0 je součástí systému Windows Vista a součástí [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].NET Framework 3,5. .NET Framework 3,5 je vyžadován pro všechny Visual Basic a vizuální C# projekty, které jsou kompilovány pro 32 operační systémy a pro které je cílové rozhraní nastaveno na **.NET Framework 3,5**, a pro Visual Basic a vizuální C# projekty zkompilované pro operační systémy s 64. (IA64 není podporováno.) Všimněte si, že Visual Basic C# a Visual projekty jsou ve výchozím nastavení kompilovány pro všechny architektury procesoru. Další informace naleznete v tématu [Přehled cílení na více platforem sady Visual Studio](../../ide/visual-studio-multi-targeting-overview.md), [Redistribuce .NET Framework](https://msdn.microsoft.com/a18d0456-fd89-493e-97f4-756505bfe287)a [nasazení požadavků pro 64 aplikace](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Ve výchozím nastavení je tato položka vybraná.|
|**Profil klienta .NET Framework 3,5 SP1**|Profil klienta .NET Framework je podmnožinou úplné .NET Framework 3,5 SP1, která cílí na klientské aplikace. Poskytuje zjednodušenou podmnožinu funkcí Windows Presentation Foundation (WPF), model Windows Forms, Windows Communication Foundation (WCF) a ClickOnce. To umožňuje scénáře rychlého nasazení pro WPF, model Windows Forms, WCF a konzolové aplikace, které cílí na .NET Framework profil klienta. Další informace najdete v tématu [.NET Framework profil klienta](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).|
|**Microsoft .NET Framework 4 (x86 a x64)**|Tento balíček nainstaluje .NET Framework 4 pro platformy x86 i x64.<br /><br /> Další informace naleznete v tématu [Přehled cílení na více platforem sady Visual Studio](../../ide/visual-studio-multi-targeting-overview.md), [Redistribuce .NET Framework](https://msdn.microsoft.com/a18d0456-fd89-493e-97f4-756505bfe287)a [nasazení požadavků pro 64 aplikace](../../deployment/deploying-prerequisites-for-64-bit-applications.md).<br /><br /> Ve výchozím nastavení je tato položka vybraná.|
|**Profil klienta Microsoft .NET Framework 4 (x86 a x64)**|Profil klienta .NET Framework 4 je podmnožinou úplné .NET Framework 4, která cílí na klientské aplikace. Poskytuje zjednodušenou podmnožinu funkcí Windows Presentation Foundation (WPF), model Windows Forms, Windows Communication Foundation (WCF) a ClickOnce. To umožňuje scénáře rychlého nasazení pro WPF, model Windows Forms a konzolové aplikace, které cílí na profil klienta .NET Framework 4. Další informace najdete v tématu [.NET Framework profil klienta](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).|
|**systém Microsoft Office 2007 primárních sestavení vzájemné spolupráce**|Tento balíček nainstaluje primární spolupracující sestavení pro produkty 2007 systém Microsoft Office. Primární definiční sestavení umožňuje spravovanému kódu pracovat s modelem objektů založenými na modelu COM systém Microsoft Office aplikace. Další informace najdete v tématu [primární spolupracující sestavení pro Office](https://msdn.microsoft.com/library/aa29d12c-185f-4558-a7cd-3d85f924203d).|
|**Microsoft Visual Basic PowerPacks verze 10,0**|Sady Power Pack jsou doplňky, ovládací prvky, komponenty a nástroje, které vám pomůžou při vývoji aplikací Visual Basic. Tato verze obsahuje komponentu [PrintForm](/previous-versions/bb882742(v=vs.140)) , která umožňuje vytisknout obsah formuláře Windows a knihovnu kompatibility tiskáren, která umožňuje, aby se kód tiskárny Visual Basic 6,0 nezměnil.|
|**Microsoft Visual F# runtime pro .NET 2,0**|Tento balíček nainstaluje Visual F# runtime knihovny pro operační systémy x86 a x64, které poskytují podporu pro funkční programování a také tradiční programování orientované na objekty a imperativní (procedurální). Tento balíček musí být nainstalován, pokud aplikace nebo její součásti jsou vytvořeny v jazyce Visual F# a .NET Framework 2,0, .NET Framework 3,0 nebo .NET Framework 3,5.<br /><br /> Další informace najdete v tématu [ F# Referenční dokumentace jazyka](https://msdn.microsoft.com/library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|
|**Microsoft Visual F# runtime pro .NET 4,0**|Tento balíček nainstaluje Visual F# runtime knihovny pro operační systémy x86 a x64, které poskytují podporu pro funkční programování a také tradiční programování orientované na objekty a imperativní (procedurální). Tento balíček musí být nainstalován, pokud aplikace nebo její součásti jsou vytvořeny v jazyce Visual F# a .NET Framework 4.<br /><br /> Další informace najdete v tématu [ F# Referenční dokumentace jazyka](https://msdn.microsoft.com/library/16b706f8-b5f2-4ff7-b2c1-64df33cd6adf).|
|**Microsoft Visual Studio 2010 Report Viewer**|Tento balíček nainstaluje ovládací prvky prohlížeče sestav, které můžete použít k přidání bohatých sestav dat do aplikací model Windows Forms a ASP.NET.|
|**Microsoft Visual Studio 2010 pro prostředí Office runtime (x86 a x64)**|Nástroje Office Developer Tools v sadě Visual Studio nabízí snadno použitelné a integrované nástroje pro vytváření vlastních obchodních řešení pomocí systém Microsoft Office. Můžete vytvářet spravovaná inteligentní klientská řešení, která aplikace Office používají jako uživatelské rozhraní. Nástroje umožňují vývojářům vytvářet zabezpečená řešení, která se dají snadno nasazovat a udržovat.<br /><br /> Další informace naleznete v tématu [How to: Publishing a řešení Office using ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).|
|**SQL Server 2005 Express Edition SP2 (x86)**|Tento balíček nainstaluje Microsoft SQL Server 2005 Express Edition SP2, databázovou aplikaci založenou na [!INCLUDE[sqprsqext](../../includes/sqprsqext-md.md)]. SQL Server Express je náhrada pro Microsoft SQL Server Desktop Engine (MSDE). SQL Server Express je zdarma a je možné ho znovu distribuovat (podléhající smlouvě) a funguje jako klientská databáze i základní databáze serveru. Je stejný jako SQL Server 2005, s výjimkou následujících rozdílů:<br /><br /> -Žádné podnikové funkce nepodporují.<br />– Omezeno na jeden procesor.<br />– omezení velikosti paměti pro fond vyrovnávacích pamětí: 1 gigabajt (GB).<br />-4 GB maximální velikost pro databáze.|
|**SQL Server 2008 Express**|Tento balíček nainstaluje Microsoft SQL Server 2008 Express, bezplatnou edici Microsoft SQL Server 2008, což je ideální databáze pro malé webové, serverové nebo desktopové aplikace. Dá se použít zdarma pro vývoj a produkci. K distribuci SQL Server 2008 Express s aplikací se vyžaduje bezplatná registrace.<br /><br /> Chování zaváděcího nástroje je následující:<br /><br /> – Pokud už počítač má SQL Server 2008 Express nebo novější, zůstane počítač v SQL Server 2008 Express nebo novějším.<br />– Pokud počítač nemá žádnou verzi SQL Server 2008 Express nebo novější, balíček nainstaluje nejnovější verzi SQL Server 2008 Express SP1.<br /><br /> Další informace o SQL Server 2008 Express najdete v [http://go.microsoft.com/fwlink/?LinkId=183586](https://go.microsoft.com/fwlink/?LinkId=183586).|
|**Běhové knihovny Visual C++ 2010 (IA64)**|Tento balíček nainstaluje Visual C++ runtime knihovny pro architekturu Itanium, která poskytuje rutiny pro programování pro operační systém Microsoft Windows. Tyto rutiny automatizují mnoho běžných programovacích úloh, které nejsou poskytovány jazyky C C++ a.<br /><br /> Další informace najdete v tématu Referenční dokumentace běhové [knihovny jazyka C](https://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|
|**Běhové knihovny Visual C++ 2010 (x64)**|Tento balíček nainstaluje Visual C++ běhové knihovny pro operační systémy x64, které poskytují rutiny pro programování pro operační systém Microsoft Windows. Tyto rutiny automatizují mnoho běžných programovacích úloh, které nejsou poskytovány jazyky C C++ a.<br /><br /> Další informace najdete v tématu Referenční dokumentace běhové [knihovny jazyka C](https://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|
|**Běhové knihovny Visual C++ 2010 (x86)**|Tento balíček nainstaluje Visual C++ běhové knihovny pro operační systémy x86, které poskytují rutiny pro programování pro operační systém Microsoft Windows. Tyto rutiny automatizují mnoho běžných programovacích úloh, které nejsou poskytovány jazyky C C++ a.<br /><br /> Další informace najdete v tématu Referenční dokumentace běhové [knihovny jazyka C](https://msdn.microsoft.com/library/a503e11c-8dca-4846-84fb-025a826c32b8).|
|**Instalační služba systému Windows 3,1**|Tento balíček nainstaluje Microsoft Instalační služba systému Windows Redistributable, verze 3,1, která umožňuje instalaci Instalační služba systému Windows instalačních projektů. Je předinstalována v systému Windows Server 2003 s aktualizací SP1 a novější.<br /><br /> Ve výchozím nastavení je tato položka vybraná.|
|**Instalační služba systému Windows 4,5**|Tento balíček nainstaluje Microsoft Instalační služba systému Windows Redistributable, verze 4,5, která umožňuje instalaci Instalační služba systému Windows instalačních projektů.|

## <a name="see-also"></a>Viz také
 [Stránka publikování, nasazení aplikace Návrhář projektu](../../ide/reference/publish-page-project-designer.md) [požadavky](../../deployment/application-deployment-prerequisites.md) [Redistribuce .NET Framework](https://msdn.microsoft.com/a18d0456-fd89-493e-97f4-756505bfe287) [nasazení požadavků pro 64](../../deployment/deploying-prerequisites-for-64-bit-applications.md) . [Visual Studio – Přehled cílení na více](../../ide/visual-studio-multi-targeting-overview.md) platforem
