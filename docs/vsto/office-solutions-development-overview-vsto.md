---
title: Přehled vývoje řešení pro Office (VSTO)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies, Office
- Office development in Visual Studio, about developing solutions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3586d6bc141992d7d8fe4629e7f56d04e4e247aa
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672623"
---
# <a name="office-solutions-development-overview-vsto"></a>Přehled vývoje řešení pro Office (VSTO)
  Pomocí aplikace Microsoft Office jako front-endu řešení, můžete využít známé uživatelské rozhraní aplikace Microsoft Office a nástrojů, jako jsou funkce zpracování textu ve Wordu, funkce pro analýzu dat aplikace Excel a funkcím pro správu e-mailu aplikace Outlook . Můžete vyvíjet řešení v sadě Visual Studio k přizpůsobení aplikace Office a přidejte konkrétní funkce, které potřebujete pro své podnikové procesy. Například můžete zapnout Word do smlouvy generátor, který sestaví kontrakty si již existující částí, které mohou být provedeny upravovatelného nebo nejde upravit. Pomocí aplikace Excel můžete vytvořit přizpůsobené pro různé projekty listu aplikace automatizované rozpočtu. Uživatelům můžete taky využít řešení pro systém office v režimu offline, což je komplexní řešení více praktické, než by se použily, pokud používáte architekturu založenou na web.  
  
 Toto téma obsahuje přehled typů řešení pro Office můžete vytvořit pomocí nástroje Visual Studio Tools pro Office (VSTO) šablony jsou dostupné v Office developer tools v sadě Visual Studio. Obecné informace o vývoji s Office, najdete v článku [střediska pro vývojáře Office](https://dev.office.com/).  
  
## <a name="choose-an-office-project-type"></a>Zvolte typ projektu Office  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] poskytuje následující typy šablon projektů pro vývoj pro Office na základě VSTO:  
  
- **Přizpůsobení na úrovni dokumentu** jsou spojeny s určitým dokumentem.  
  
- **Doplňky VSTO** jsou spojeny s vlastní aplikace.  
  
  Rozhodnout, které tyto typy projektů je nejvhodnější pro vaše řešení, zamyslete se, jestli chcete spustit kód jenom v případě určitého dokumentu je otevřený nebo, jestli chcete, aby byl kód k dispozici vždy, když je aplikace spuštěna. Další informace o šablonách projektů, naleznete v tématu [Přehled šablon projektů Office project](../vsto/office-project-templates-overview.md).  
  
  Typy projektů, které můžete vytvořit závisí na aplikace Office, které jste nainstalovali na vývojovém počítači. Další informace najdete v tématu [dostupné funkce podle typu aplikace a projekt sady Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
### <a name="document-level-customizations"></a>Přizpůsobení na úrovni dokumentu  
 Přizpůsobení na úrovni dokumentu se skládají z sestavení, který je přidružený jeden dokument, sešit nebo šablonu v Microsoft Office Word nebo Microsoft Office Excel. Sestavení je načteno při otevření přidružený dokument. Funkce úpravy, které vytvoříte jsou k dispozici pouze v případě, že související dokument je otevřen. Přizpůsobení nemůže provádět změny celou aplikaci, jako je například zobrazení na nové kartě položky nebo pás karet nabídky při jakýkoliv dokument je otevřen.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obsahuje nástroje, které pomáhají vytvářet přizpůsobení na úrovni dokumentu. Dokument, který upravíte je hostovaný jako návrhovou plochu v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], což vám umožní navrhnout dokumentu přetažením ovládacích prvků na něj. Mnoho dalších [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] funkce jsou k dispozici v projektech na úrovni dokumentu, jako je například ovládací prvky Windows Forms, přetáhněte myší datové vazby a integrovaný ladicí program.  
  
 Další informace o přizpůsobení najdete v následujících tématech:  
  
-   [Začínáme s programováním přizpůsobení na úrovni dokumentu pro Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)  
  
-   [Začínáme s programováním přizpůsobení na úrovni dokumentu pro Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)  
  
-   [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md)  
  
### <a name="vsto-add-ins"></a>Doplňky VSTO  
 Doplňky VSTO obsahovat sestavení, který je přidružen k aplikaci Microsoft Office. Obvykle doplňku VSTO spustí při spuštění přidružené aplikace, i když se uživatelé můžou také doplňků VSTO po načtení aplikace je už spuštěná. Funkce doplňků VSTO, které vytvoříte jsou k dispozici pro aplikace, samostatně, bez ohledu na to, které jsou otevřené dokumenty.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] obsahuje nástroje, které pomáhají při vytváření doplňků VSTO. Projekty doplňků zahrnují automaticky generované třídy, která představuje doplňku VSTO. Tato třída obsahuje vlastnosti a události, které můžete použít pro přístup k modelu objektu hostitelské aplikace a spuštění kódu pokud doplňku VSTO je načten a vypnout. Mnoho dalších [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] funkce jsou k dispozici v doplňku VSTO projekty, jako jsou Windows Forms a integrovaný ladicí program.  
  
 Další informace o doplňcích VSTO naleznete v následujících tématech:  
  
-   [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
-   [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Automatizace aplikací Office pomocí primárních sestavení vzájemné spolupráce  
 Do vašeho řešení prostřednictvím kódu programu napsáním kódu, který má přístup k aplikačním objektový model začlenit funkce aplikace Office. Objektové modely jsou uspořádání tříd, které zprostředkovávají funkce prostřednictvím různých vlastností a metod. Objektový model pro každou aplikaci sady Office se liší.  
  
 Chcete-li použít objektový model aplikace sady Office z řešení vytvořené pomocí nástrojů pro vývoj pro Office v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], je nutné použít sestavení primární spolupráce (PIA) pro aplikaci. PIA umožňuje spravovanému kódu ve vašem řešení k interakci s aplikací Office COM založené na objektovém modelu.  
  
 PIA pro systém Office nainstalována a zaregistrována v globální mezipaměti sestavení na vašem vývojovém počítači provádět většinu vývojářských úkolů musíte mít. Další informace najdete v tématu [konfigurace počítače pro vývoj řešení pro systém Office](../vsto/configuring-a-computer-to-develop-office-solutions.md). Sestavení PIA sady Office nejsou vyžadovány v počítačích koncových uživatelů pro spuštění řešení pro systém Office VSTO. Další informace najdete v tématu [návrhu a vytvořte řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md).  
  
 Další informace o použití sestavení PIA v řešeních pro systém Office VSTO naleznete v následujících tématech:  
  
-   [Psaní kódu v řešeních pro systém Office](../vsto/writing-code-in-office-solutions.md)  
  
-   [Primární spolupracující sestavení Office](../vsto/office-primary-interop-assemblies.md)  
  
## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Spustit řešení sady Office Microsoft VSTO na počítačích koncových uživatelů  
 Když vytvoříte řešení VSTO Office, zvažte, jak požadavky na nasazení může ovlivnit vaše možnosti vývoje.  
  
### <a name="deployment-options"></a>Možnosti nasazení  
 Použít ClickOnce nebo instalační služby systému Windows k nasazení řešení, které vytvoříte pomocí nástrojů pro vývoj pro Office v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. ClickOnce – nasazení umožňuje vytvářet řešení automatických aktualizací, které mohou být nainstalovány a spuštění vyžadují minimální interakci uživatele. Instalační služby systému Windows (*MSI*) soubory mohou být snadno distribuovat do počítače koncového uživatele, nebo distribuována pomocí Systems Management Server (SMS). Další informace o nasazení řešení VSTO Office najdete v tématu [nasazení řešení Office](../vsto/deploying-an-office-solution.md).  
  
### <a name="install-prerequisites"></a>Instalace požadovaných součástí  
 Koncoví uživatelé mohli spustit řešení můžete vytvořit pomocí nástrojů pro vývoj pro Office v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], jejich počítače musí mít nainstalovány některé požadované součásti. Pokud vaše řešení nasadit, s použitím technologie ClickOnce nebo vytvořením souboru Instalační služby systému Windows, tyto požadavky lze nainstalovat v rámci řešení. Další informace najdete v tématu [požadavky řešení Office na nasazení](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e) a [postupy: instalace požadovaných součástí na počítačích koncových uživatelů, které spouštějí řešení Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
### <a name="security"></a>Zabezpečení  
 Zabezpečení pro řešení pro systém Office VSTO jsou vynuceny řadu kontroluje, zda [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] při instalaci a načtení řešení. Mezi tyto kontroly patří ověření, zda je umístění manifestu nasazení důvěryhodné nebo určuje, zda je důvěryhodný certifikát použitý k podepsání manifestu nasazení. Další informace najdete v tématu [řešení pro systém Office zabezpečení](../vsto/securing-office-solutions.md).  
  
## <a name="see-also"></a>Viz také:  
 [Začínáme &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md)   
 [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Začínáme s programováním přizpůsobení na úrovni dokumentu pro Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)   
 [Začínáme s programováním přizpůsobení na úrovni dokumentu pro Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)   
 [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  