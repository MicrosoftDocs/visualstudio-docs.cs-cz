---
title: Přehled vývoje řešení pro systém Office (VSTO)
description: Naučte se vyvíjet vlastní nastavení pro známá systém Microsoft Office uživatelská rozhraní a nástroje, jako jsou funkce pro zpracování slov ve Wordu a funkce analýzy dat v Excelu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies, Office
- Office development in Visual Studio, about developing solutions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 03da1c8052140bbe23ce4d99c12d72baef18898f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891953"
---
# <a name="office-solutions-development-overview-vsto"></a>Přehled vývoje řešení pro systém Office (VSTO)
  Pomocí systém Microsoft Office jako front-endu pro řešení můžete využít výhod známých systém Microsoft Office uživatelských rozhraní a nástrojů, jako jsou funkce pro zpracování slov ve Wordu, funkce analýzy dat Excelu a funkce pro správu e-mailu v Outlooku. V sadě Visual Studio můžete vyvíjet řešení pro přizpůsobení aplikací Office a přidání specifických funkcí, které pro své obchodní procesy potřebujete. Můžete například změnit slovo na generátor smluv, který sestaví smlouvy mimo již existující části, které lze upravovat nebo nelze upravovat. V aplikaci Excel můžete vytvořit automatický sešit rozpočtu přizpůsobený pro různé projekty. Uživatelé mohou také řešení Office přijímat v režimu offline, což usnadňuje složitější řešení, než by se používala při použití webové architektury.

 Toto téma poskytuje přehled typů řešení pro systém Office, které můžete vytvořit pomocí šablon Visual Studio Tools for Office (VSTO) dostupných v sadě Office Developer Tools v sadě Visual Studio. Obecné informace o tom, jak vyvíjet v Office, najdete v [centru vývojářů pro Office](https://developer.microsoft.com/office).

## <a name="choose-an-office-project-type"></a>Zvolit typ projektu Office
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] poskytuje následující typy šablon projektů pro vývoj pro Office založené na VSTO:

- **Přizpůsobení na úrovni dokumentu** jsou přidružena k určitému dokumentu.

- **Doplňky VSTO** jsou přidruženy k samotné aplikaci.

  Chcete-li určit, který z těchto typů projektů je nejvhodnější pro vaše řešení, zamyslete se, zda má být kód spuštěn pouze v případě, že je otevřen konkrétní dokument, nebo zda má být kód k dispozici vždy, když je aplikace spuštěna. Další informace o šablonách projektů naleznete v tématu [Přehled šablon projektů Office](../vsto/office-project-templates-overview.md).

  Typy projektů, které můžete vytvořit, závisí na tom, jaké aplikace Office jste nainstalovali do vývojového počítače. Další informace najdete v tématu [dostupné funkce podle aplikace systému Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

### <a name="document-level-customizations"></a>Přizpůsobení na úrovni dokumentu
 Přizpůsobení na úrovni dokumentu se skládá ze sestavení, které je přidruženo k jednomu dokumentu, sešitu nebo šabloně v aplikaci systém Microsoft Office Word nebo systém Microsoft Office Excel. Sestavení je načteno při otevření přidruženého dokumentu. Funkce vlastního nastavení, které vytvoříte, jsou k dispozici pouze v případě, že je přidružený dokument otevřen. Vlastní nastavení nemůže dělat změny v rámci aplikace, jako je například zobrazení nové položky nabídky nebo karty pásu karet, když je otevřen libovolný dokument.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obsahuje nástroje, které vám pomůžou vytvářet přizpůsobení na úrovni dokumentu. Dokument, který přizpůsobíte, je hostovaný jako návrhová plocha v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , která umožňuje návrh dokumentu přetažením ovládacích prvků na něj. Mnoho dalších [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] funkcí je dostupných v projektech na úrovni dokumentu, jako jsou model Windows Forms ovládací prvky, přetahování datových vazeb a integrovaný ladicí program.

 Další informace o přizpůsobeních naleznete v následujících tématech:

- [Začínáme s programováním přizpůsobení na úrovni dokumentu pro Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)

- [Začínáme programovat přizpůsobení na úrovni dokumentu pro Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)

- [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md)

### <a name="vsto-add-ins"></a>Doplňky VSTO
 Doplňky VSTO se skládají ze sestavení, které je přidružené k aplikaci systém Microsoft Office. Doplněk VSTO se obvykle spouští při spuštění přidružené aplikace, i když uživatelé můžou načítat doplňky VSTO i po tom, co už je aplikace spuštěná. Funkce v doplňcích VSTO, které vytvoříte, jsou k dispozici pro samotnou aplikaci, bez ohledu na to, které dokumenty jsou otevřené.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obsahuje nástroje, které vám pomůžou vytvářet doplňky VSTO. Projekty doplňku obsahují automaticky generovanou třídu, která představuje doplněk VSTO. Tato třída poskytuje vlastnosti a události, které lze použít pro přístup k objektovému modelu hostitelské aplikace a spuštění kódu při načtení a vypnutí doplňku VSTO. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]V projektech doplňku VSTO je k dispozici řada dalších funkcí, například model Windows Forms a integrovaný ladicí program.

 Další informace o doplňcích VSTO najdete v následujících tématech:

- [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)

- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)

## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Automatizace aplikací Office pomocí primárních sestavení vzájemné spolupráce
 Do svého řešení můžete programově začlenit funkce aplikace Office, a to psaním kódu, který přistupuje k objektovému modelu aplikace. Objektové modely jsou uspořádání tříd, které zpřístupňují funkce prostřednictvím různých vlastností a metod. Objektový model pro každou aplikaci Office je jiný.

 Chcete-li použít objektový model aplikace sady Office z řešení vytvořeného pomocí nástrojů pro vývoj pro Office v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , je nutné pro aplikaci použít primární definiční sestavení (PIA). PIA umožňuje spravovanému kódu ve vašem řešení pracovat s modelem objektu založeným na modelu COM aplikace Office.

 Abyste mohli provádět většinu vývojářských úloh, musíte mít nainstalovanou a zaregistrované PIA Office v globální mezipaměti sestavení (GAC) ve vývojovém počítači. Další informace najdete v tématu [Konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md). Pro spouštění řešení VSTO Office se na počítačích koncových uživatelů nevyžadují PIA Office. Další informace najdete v tématu [Návrh a vytváření řešení pro Office](../vsto/designing-and-creating-office-solutions.md).

 Další informace o použití PIA v řešeních pro Office VSTO najdete v následujících tématech:

- [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)

- [Sestavení primární spolupráce pro Office](../vsto/office-primary-interop-assemblies.md)

## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Spuštění řešení Microsoft VSTO Office na počítačích koncových uživatelů
 Když vytvoříte řešení Office VSTO, zvažte, jak můžou požadavky na nasazení ovlivnit vaše možnosti vývoje.

### <a name="deployment-options"></a>Možnosti nasazení
 Pomocí technologie ClickOnce nebo Instalační služba systému Windows můžete nasadit řešení vytvořená pomocí vývojářských nástrojů pro Office v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Nasazení ClickOnce umožňuje vytvořit řešení s automatickými aktualizacemi, která se dají nainstalovat a spustit s minimální interakcí uživatelů. Soubory Instalační služba systému Windows (*. msi*) je možné snadno distribuovat do počítačů koncových uživatelů nebo distribuovat pomocí serveru pro správu systému (SMS). Další informace o nasazení řešení VSTO Office najdete v tématu [nasazení řešení pro Office](../vsto/deploying-an-office-solution.md).

### <a name="install-prerequisites"></a>Požadavky na instalaci
 Předtím, než mohou koncoví uživatelé spustit řešení, které vytvoříte pomocí nástrojů pro vývoj pro Office v nástroji [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , musí mít jejich počítače nainstalovány určité požadavky. Pokud nasadíte řešení pomocí technologie ClickOnce nebo vytvořením souboru Instalační služba systému Windows, tyto požadavky lze nainstalovat s vaším řešením. Další informace najdete v tématu [předpoklady pro řešení Office pro nasazení](/previous-versions/bb608617(v=vs.110)) a [Postupy: instalace požadovaných součástí na počítačích koncových uživatelů ke spouštění řešení pro Office](/previous-versions/bb608608(v=vs.110)).

### <a name="security"></a>Zabezpečení
 Zabezpečení pro řešení VSTO Office se vynutilo řadou kontrol, které [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] při instalaci a načtení řešení vytvoří. Tyto kontroly zahrnují ověření, zda je umístění manifestu nasazení důvěryhodné nebo zda certifikát použitý k podepsání manifestu nasazení je důvěryhodný. Další informace najdete v tématu [zabezpečení řešení pro Office](../vsto/securing-office-solutions.md).

## <a name="see-also"></a>Viz také
- [Začněte &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Začínáme s programováním přizpůsobení na úrovni dokumentu pro Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Začínáme programovat přizpůsobení na úrovni dokumentu pro Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
