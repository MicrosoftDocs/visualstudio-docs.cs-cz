---
title: Přehled vývoje kancelářských řešení (VSTO)
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: abb58d30e33ab5cfe713175b40cd32f593921ae9
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543952"
---
# <a name="office-solutions-development-overview-vsto"></a>Přehled vývoje kancelářských řešení (VSTO)
  Pomocí sady Microsoft Office jako front-endu pro řešení můžete využít známých uživatelských rozhraní a nástrojů sady Microsoft Office, jako jsou funkce zpracování textu v aplikaci Word, funkce analýzy dat aplikace Excel a funkce správy e-mailů aplikace Outlook. V sadě Visual Studio můžete vyvíjet řešení pro přizpůsobení aplikací Office a přidání specifických funkcí, které potřebujete pro vaše obchodní procesy. Můžete například změnit aplikaci Word na generátor smluv, který sestavuje smlouvy z již existujících součástí, které lze upravit nebo je nelze upravit. V aplikaci Excel můžete vytvořit automatizovaný rozpočtový list přizpůsobený pro různé projekty. Vaši uživatelé mohou také přepnout kancelářská řešení do provozu offline, což činí komplexní řešení praktičtějšími, než by byla, pokud používáte webovou architekturu.

 Toto téma obsahuje přehled typů řešení Office, které můžete vytvořit pomocí šablon Visual Studio Tools for Office (VSTO), které jsou k dispozici v vývojářských nástrojích Office v sadě Visual Studio. Obecné informace o vývoji pomocí Office najdete v centru [pro vývojáře Office](https://developer.microsoft.com/office).

## <a name="choose-an-office-project-type"></a>Volba typu projektu Office
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]poskytuje následující typy šablon projektů pro vývoj sady Office založené na vsto:

- **Vlastní nastavení na úrovni dokumentu** jsou přidružena k určitému dokumentu.

- **Doplňky VSTO** jsou přidruženy k samotné aplikaci.

  Chcete-li se rozhodnout, který z těchto typů projektů je nejvhodnější pro vaše řešení, přemýšlejte o tom, zda chcete, aby byl kód spuštěn pouze v případě, že je otevřený určitý dokument, nebo zda chcete, aby byl kód k dispozici při každém spuštění aplikace. Další informace o šablonách projektů najdete v tématu [Přehled šablon projektů sady Office](../vsto/office-project-templates-overview.md).

  Typy projektů, které můžete vytvořit, závisí na tom, které aplikace sady Office jste nainstalovali do vývojového počítače. Další informace naleznete v [tématu Funkce dostupné aplikací sady Office a typu projektu](../vsto/features-available-by-office-application-and-project-type.md).

### <a name="document-level-customizations"></a>Přizpůsobení na úrovni dokumentu
 Vlastní nastavení na úrovni dokumentu se skládá ze sestavy přidružené k jedinému dokumentu, sešitu nebo šabloně v aplikaci Microsoft Office Word nebo Microsoft Office Excel. Sestavení se načte při otevření přidruženého dokumentu. Funkce v úpravách, které vytvoříte, jsou k dispozici pouze v případě, že je otevřený přidružený dokument. Vlastní nastavení nemůže provádět změny v rámci celé aplikace, například zobrazení nové položky nabídky nebo karty pásu karet při otevření libovolného dokumentu.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]obsahuje nástroje, které vám pomohou vytvořit vlastní nastavení na úrovni dokumentu. Dokument, který vlastníte, je hostován jako návrhová plocha v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]aplikaci , což umožňuje navrhnout dokument přetažením ovládacích prvků na něj. Mnoho [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dalších funkcí je k dispozici v projektech na úrovni dokumentu, jako jsou ovládací prvky Windows Forms, datové vazby přetažení a integrovaný ladicí program.

 Další informace o vlastních nastaveních naleznete v následujících tématech:

- [Začínáme s programováním vlastního nastavení na úrovni dokumentů pro Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)

- [Začínáme s programováním vlastního nastavení na úrovni dokumentů pro Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)

- [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md)

### <a name="vsto-add-ins"></a>Doplňky VSTO
 Doplňky VSTO se skládají ze sestavení, které je přidruženo k aplikaci sady Microsoft Office. Doplněk VSTO se obvykle spustí při spuštění přidružené aplikace, i když uživatelé mohou také načíst doplňky VSTO po spuštění aplikace. Funkce v doplňcích VSTO, které vytvoříte, jsou k dispozici pro samotnou aplikaci bez ohledu na to, které dokumenty jsou otevřené.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]obsahuje nástroje, které vám pomohou vytvořit doplňky VSTO. Projekty doplňků zahrnují automaticky generovanou třídu, která představuje doplněk VSTO. Tato třída poskytuje vlastnosti a události, které můžete použít pro přístup k objektovému modelu hostitelské aplikace a spustit kód při načtení a vypnutí doplňku VSTO. Mnoho [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dalších funkcí je k dispozici v projektech doplňků VSTO, jako jsou windows forms a integrovaný ladicí program.

 Další informace o doplňcích VSTO naleznete v následujících tématech:

- [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)

- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)

## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Automatizace aplikací Office pomocí primárních interop sestav
 Můžete programově začlenit funkce aplikace sady Office do vašeho řešení zápisem kódu, který přistupuje k objektového modelu aplikace. Objektové modely jsou uspořádání tříd, které zveřejňují funkce prostřednictvím různých vlastností a metod. Objektový model pro každou aplikaci sady Office se liší.

 Chcete-li použít objektový model aplikace sady Office z řešení [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]vytvořeného pomocí nástrojů pro vývoj sady Office v aplikaci , musíte pro aplikaci použít primární sestavení interop (PIA). PIA umožňuje spravovanému kódu ve vašem řešení pracovat s objektovým modelem založeným na com aplikace Office.

 Chcete-li provádět většinu vývojových úloh, musíte mít v globální mezipaměti sestavení ve vývojovém počítači nainstalovány a zaregistrovány certifikáty Office PIA. Další informace naleznete [v tématu Konfigurace počítače pro vývoj řešení sady Office](../vsto/configuring-a-computer-to-develop-office-solutions.md). Pia sady Office nejsou v počítačích koncových uživatelů vyžadovány ke spouštění řešení VSTO Office. Další informace naleznete v [tématu Návrh a vytvoření řešení Sady Office](../vsto/designing-and-creating-office-solutions.md).

 Další informace o používání pia v řešeních VSTO Office naleznete v následujících tématech:

- [Psaní kódu v řešeních Office](../vsto/writing-code-in-office-solutions.md)

- [Sestavy primárních meziop office](../vsto/office-primary-interop-assemblies.md)

## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Spuštění řešení Microsoft VSTO Office v počítačích koncových uživatelů
 Při vytváření řešení Sady VSTO zvažte, jak požadavky na nasazení mohou ovlivnit vaše volby vývoje.

### <a name="deployment-options"></a>Možnosti nasazení
 Pomocí Služby ClickOnce nebo Instalační služby systému Windows [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]můžete nasadit řešení, která vytvoříte pomocí nástrojů pro vývoj office v aplikaci . ClickOnce nasazení umožňuje vytvářet řešení pro vlastní aktualizaci, která lze nainstalovat a spustit s minimální interakcí uživatele. Soubory Instalační služby systému Windows (*MSI*) lze snadno distribuovat do počítačů koncových uživatelů nebo je distribuovat pomocí serveru SMS (Systems Management Server). Další informace o nasazení řešení VSTO Office najdete v [tématu Nasazení řešení Sady Office](../vsto/deploying-an-office-solution.md).

### <a name="install-prerequisites"></a>Požadavky na instalaci
 Aby koncoví uživatelé mohli spustit řešení, které [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]vytvoříte pomocí nástrojů pro vývoj sady Office v aplikaci , musí mít jejich počítače nainstalovány určité požadavky. Pokud nasadíte řešení pomocí ClickOnce nebo vytvořením souboru Instalační služby systému Windows, tyto požadavky lze nainstalovat s řešením. Další informace naleznete v [tématech Požadavky řešení Sady Office pro nasazení](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e) a [Postup: Instalace požadavků na počítače koncových uživatelů pro spuštění řešení Office](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).

### <a name="security"></a>Zabezpečení
 Zabezpečení řešení VSTO Office je vynuceno řadou [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] kontrol, které provádí při instalaci a načtení řešení. Tyto kontroly zahrnují ověření, zda je umístění manifestu nasazení důvěryhodné nebo zda je důvěryhodný certifikát použitý k podepsání manifestu nasazení. Další informace naleznete v [tématu Secure Office solutions](../vsto/securing-office-solutions.md).

## <a name="see-also"></a>Viz také
- [Začínáme &#40;vývoje ms office v&#41;Visual Studia](../vsto/getting-started-office-development-in-visual-studio.md)
- [Architektura přizpůsobení na úrovni dokumentu](../vsto/architecture-of-document-level-customizations.md)
- [Architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Začínáme s programováním vlastního nastavení na úrovni dokumentů pro Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Začínáme s programováním vlastního nastavení na úrovni dokumentů pro Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Začínáme s programováním doplňků VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
