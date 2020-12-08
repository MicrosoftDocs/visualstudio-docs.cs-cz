---
title: Sestavování řešení pro systém Office
description: Přečtěte si o rozdílech mezi vytvářením a laděním projektů Office a vytvářením a laděním jiných typů projektů v sadě Visual Studio, jako je například model Windows Forms.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- debugging [Office development in Visual Studio]
- debugging Office applications in Visual Studio
- solutions [Office development in Visual Studio], debugging
- Office applications [Office development in Visual Studio], debugging
- application development [Office development in Visual Studio], building
- Office applications [Office development in Visual Studio], building
- projects [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], building
- solutions [Office development in Visual Studio], building
- Office projects [Office development in Visual Studio], debugging
- projects [Office development in Visual Studio], building
- builds [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], building
- application development [Office development in Visual Studio], debugging
- Office solutions [Office development in Visual Studio], debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3d942a7818c3c71e0859c9271b329688734682f2
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96847933"
---
# <a name="build-office-solutions"></a>Sestavování řešení pro systém Office
  Obecně platí, že sestavování a ladění projektů Office je stejné jako vytváření a ladění jiných typů projektů v sadě Visual Studio, například model Windows Forms. Témata v této části vysvětlují rozdíly, které existují. Obecné informace o tom, jak sestavovat aplikace, najdete v tématu [kompilace a sestavování v aplikaci Visual Studio](../ide/compiling-and-building-in-visual-studio.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="project-output-for-office-projects"></a>Výstup projektu pro projekty Office
 Umístění výstupu projektů pro systém Office je *ProjectName*\bin\Release nebo *ProjectName*\bin\debug. Nelze vytvořit do adresáře nasazení.

### <a name="document-level-projects"></a>Projekty na úrovni dokumentu
 Při sestavování projektu na úrovni dokumentu jsou do výstupu projektu zahrnuty následující položky:

- Kopii dokumentu projektu.

- Sestavení projektu a všechna odkazovaná sestavení, která mají svou **místní vlastnost Copy** nastavenou na **hodnotu true**.

- Manifest aplikace, který má příponu názvu souboru *. manifest*. Další informace naleznete v tématu [manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

- Manifest nasazení, který má příponu názvu souboru *. VSTO*. Další informace najdete v tématu [manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md).

- Soubor databáze programu (*PDB*).

> [!NOTE]
> Pokud vytvoříte řešení na úrovni dokumentu ve vzdáleném umístění místo v místním počítači, přidejte plně kvalifikovanou cestu do seznamu důvěryhodných umístění v centru zabezpečení aplikace. Další informace najdete v části s názvem udělení důvěryhodnosti k dokumentům v tématu [zabezpečení řešení pro Office](../vsto/securing-office-solutions.md).

### <a name="application-level-projects"></a>Projekty na úrovni aplikace
 Při vytváření projektu doplňku VSTO jsou do výstupu projektu zahrnuty následující položky:

- Sestavení projektu a všechna odkazovaná sestavení, která mají svou **místní vlastnost Copy** nastavenou na **hodnotu true**.

- Manifest aplikace, který má příponu názvu souboru *. manifest*. Další informace naleznete v tématu [manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).

- Manifest nasazení, který má příponu názvu souboru *. VSTO*. Další informace najdete v tématu [manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md).

- Soubor databáze programu (*PDB*) pro sestavení projektu.

  Proces sestavení pro projekty doplňku VSTO také ve vývojovém počítači vytvoří sadu položek registru, které jsou nutné k načtení doplňku VSTO. Další informace najdete v tématu [položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

  Pokud vytvoříte projekt doplňku VSTO pro Outlook, který obsahuje oblasti formuláře, proces sestavení přidá do registru následující další informace:

- Klíč pro každou třídu zprávy, která je přidružena k jedné nebo více oblastem formuláře.

- Záznam pro každou oblast formuláře a přidruženou hodnotu, která představuje název doplňku VSTO pro Outlook.

  Outlook potřebuje tyto informace k načtení oblastí formuláře.

## <a name="referenced-assemblies"></a>Odkazovaná sestavení
 Můžete odkazovat na sestavení (včetně projektů knihovny tříd) z projektu vytváření řešení pro Office. Každé odkazované sestavení má vlastnost s názvem **Copy Local**. **Copy Local** označuje, zda je sestavení zkopírováno do výstupního adresáře. Ve výchozím nastavení je nastavena na **hodnotu true**. Všechna odkazovaná sestavení s **kopií Local** nastavenou na **hodnotu true** se zkopírují do výstupního adresáře.

## <a name="security-during-the-build-process"></a>Zabezpečení během procesu sestavení
 Visual Studio automaticky konfiguruje nastavení zabezpečení na vývojovém počítači, aby během procesu sestavení udělila důvěru k řešení. To umožňuje, aby se řešení spouštělo při ladění.

 Projekty Office používají certifikáty k ověření vydavatele. Sada Visual Studio automaticky vytvoří dočasný certifikát pro identifikaci řešení Office a nakonfiguruje vývojový počítač tak, aby důvěřoval dočasnému certifikátu.

 Další informace najdete v tématu [zabezpečení řešení pro Office](../vsto/securing-office-solutions.md).

### <a name="network-projects"></a>Síťové projekty
 Pokud je sestavení nebo umístění dokumentu v síťové sdílené složce, aktualizace zásad zabezpečení místní (na úrovni uživatele) není dostatečná, aby bylo možné řešení spustit. Správce musí udělit úplný vztah důvěryhodnosti na úrovni počítače do sestavení a dokumentů, které se nachází ve sdílené síťové složce ještě předtím, než se řešení spustí. Další informace o tom, jak nastavit zásady zabezpečení, najdete v tématu [zabezpečení řešení pro Office](../vsto/securing-office-solutions.md).

 Pro projekty na úrovni dokumentu musíte také přidat plně kvalifikované umístění dokumentu do seznamu důvěryhodných složek Office. Další informace najdete v tématu [udělení důvěryhodnosti k dokumentům](../vsto/granting-trust-to-documents.md).

## <a name="change-the-platform-target"></a>Změna cíle platformy
 Ve výchozím nastavení je cílová platforma pro projekty Office **Libovolný procesor**. Obvykle byste toto nastavení neměli měnit. Řešení pro systém Office, která jsou sestavená s nastavením pro všechny cílové platformy **CPU** , běží v 32 a 64 verzích Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] nebo [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] .

 Cíl platformy nastavte na hodnotu x64 pouze v případě, že vytváříte řešení, které bude spuštěno pouze v 64 verzích Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] nebo [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] , a vaše řešení volá nativní 64 rozhraní API. Další informace o tom, jak změnit nastavení cílové platformy, najdete v tématu [How to: Configure Projects to target Platforms](../ide/how-to-configure-projects-to-target-platforms.md).

 Pokud nastavíte cíl platformy na x64, řešení se nespustí v 32 verzích Windows nebo Office. Cíl platformy x64 vyžaduje, aby řešení běželo v 64m procesu.

## <a name="use-the-clean-command"></a>Použití příkazu vyčistit
 Chcete-li z vývojového počítače odebrat sestavené soubory projektu, můžete použít příkaz **vyčistit** v nabídce **sestavení** v [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Příkaz **vyčistit** odstraní všechny soubory v umístění výstupu sestavení. Pro projekty na úrovni aplikace příkaz **vyčistit** také odebere položky registru, které jsou vytvořeny procesem sestavení.

## <a name="related-topics"></a>Související témata

|Nadpis|Popis|
|-----------|-----------------|
|[Ladění projektů Office](../vsto/debugging-office-projects.md)|Prezentují problémy spojené s laděním projektů Office.|
|[Návod: vytvoření prvního přizpůsobení na úrovni dokumentu pro Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Ukazuje, jak vytvořit základní přizpůsobení na úrovni dokumentu pro aplikaci Excel.|
|[Postupy: opětovné povolení zakázaného doplňku VSTO](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Popisuje, jak znovu povolit doplněk VSTO, který byl pevný nebo měkký.|
|[Návrh a tvorba řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)|Obsahuje odkazy na informace o vytváření řešení pro systém Office a o rolích sestavení ve vašem řešení.|