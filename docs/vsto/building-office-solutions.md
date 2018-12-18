---
title: Vytváření řešení pro systém Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 989014bb512ec77af908d823390b1e95b9a7872c
ms.sourcegitcommit: 20c0991d737c540750c613c380cd4cf5bb07de51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53248228"
---
# <a name="build-office-solutions"></a>Vytváření řešení pro systém Office
  Obecně platí sestavování a ladění projektů Office je stejná jako sestavování a ladění ostatních typů projektů v sadě Visual Studio, jako jsou Windows Forms. Témata v této části popisují, které existují rozdíly. Obecné informace o tom, jak vytvářet aplikace, najdete v části [kompilace a sestavení v sadě Visual Studio](/visualstudio/ide/compiling-and-building-in-visual-studio).  
  
> [!NOTE]  
>  Zajímá vás vývoj řešení, které rozšiřují Office prostředí napříč [více platforem](https://dev.office.com/add-in-availability)? Podívejte se na nové [Office Add-ins modelu](https://dev.office.com/docs/add-ins/overview/office-add-ins). Doplňky sady Office mají malé náklady v porovnání s doplňky VSTO a řešení a je můžete vytvořit s využitím téměř jakékoli webové programování technologie, jako je například HTML5, JavaScript, CSS3 a XML.  
  
## <a name="project-output-for-office-projects"></a>Výstup projektu pro projekty pro systém Office  
 Je umístění výstupu pro projekty Office *projectname*\bin\release nebo *projectname*\bin\debug. Nelze sestavit do adresáře nasazení.  
  
### <a name="document-level-projects"></a>Projekty na úrovni dokumentu  
 Při vytváření projektu úrovni dokumentu ve výstupu projektu zahrnuje následující položky:  
  
-   Kopii dokumentu projektu.  
  
-   Sestavení projektu se všemi odkazovanými sestaveními, které mají jejich **Kopírovat místně** vlastnost nastavena na hodnotu **true**.  
  
-   Manifest aplikace, který má příponu názvu souboru *.manifest*. Další informace najdete v tématu [manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).  
  
-   Manifest nasazení, který má příponu názvu souboru *.vsto*. Další informace najdete v tématu [manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
-   Databáze programu (*PDB*) soubor.  
  
> [!NOTE]  
>  Pokud vytváříte úrovni dokumentu řešení do vzdáleného umístění, namísto místního počítače, přidejte plně kvalifikovanou cestu do seznamu důvěryhodných umístění v Centru zabezpečení aplikace. Další informace najdete v tématu části udělení vztah důvěryhodnosti s dokumenty v [řešení pro systém Office zabezpečení](../vsto/securing-office-solutions.md).  
  
### <a name="application-level-projects"></a>Projekty na úrovni aplikace  
 Při vytváření projektu doplňku VSTO ve výstupu projektu zahrnuje následující položky:  
  
- Sestavení projektu se všemi odkazovanými sestaveními, které mají jejich **Kopírovat místně** vlastnost nastavena na hodnotu **true**.  
  
- Manifest aplikace, který má příponu názvu souboru *.manifest*. Další informace najdete v tématu [manifesty aplikace pro řešení Office](../vsto/application-manifests-for-office-solutions.md).  
  
- Manifest nasazení, který má příponu názvu souboru *.vsto*. Další informace najdete v tématu [manifesty nasazení pro řešení Office](../vsto/deployment-manifests-for-office-solutions.md).  
  
- Databáze programu (*PDB*) soubor pro sestavení projektu.  
  
  Proces sestavení pro projekty doplňků VSTO také vytvoří sadu položky registru na vývojovém počítači, které jsou nutné k načtení doplňku VSTO. Další informace najdete v tématu [položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
  Pokud vytvoříte projekt doplňku VSTO pro Outlook, který obsahuje oblasti formuláře, proces sestavení přidá do registru následující doplňkové informace:  
  
- Klíč pro každou třídu zpráv, který je přidružený jeden nebo více oblastí formulářů.  
  
- Záznam pro každou oblast formuláře a přidruženou hodnotu, která představuje název doplňku VSTO v Outlooku.  
  
  Outlook musí tyto informace načíst oblasti formuláře.  
  
## <a name="referenced-assemblies"></a>Odkazovaná sestavení  
 Z projektu sestavování řešení pro Office můžete odkazovat na sestavení (včetně projekty knihovny tříd). Všechna odkazovaná sestavení má vlastnost s názvem **Kopírovat místně**. **Kopírovat místní** označuje, zda sestavení je zkopírován do výstupního adresáře. Ve výchozím nastavení nastavena na **true**. Všechna odkazovaná sestavení, který má **Kopírovat místně** nastavena na **true** je zkopírován do výstupního adresáře.  
  
## <a name="security-during-the-build-process"></a>Zabezpečení během procesu sestavení  
 Visual Studio automaticky nakonfiguruje nastavení zabezpečení na vývojovém počítači zajištění důvěryhodnosti řešení během procesu sestavení. To umožňuje řešení pro spouštění během ladění.  
  
 Projekty Office používat certifikáty k ověření vydavatele. Visual Studio automaticky vytvoří dočasné certifikátu můžete identifikovat řešení pro systém Office a nakonfiguruje vývojového počítače do dočasné certifikátu důvěřovat.  
  
 Další informace najdete v tématu [řešení pro systém Office zabezpečení](../vsto/securing-office-solutions.md).  
  
### <a name="network-projects"></a>Projekty sítí  
 Pokud je umístění sestavení nebo dokumentu do sdílené síťové složky, místní aktualizace zásad zabezpečení (na úrovni uživatele) není dostatečně k povolení spuštění řešení. Správce musí udělit úplný vztah důvěryhodnosti na úrovni počítače pro sestavení a dokumenty, které jsou ve sdílené síťové složce, než se spustí řešení. Další informace o tom, jak nastavit zásady zabezpečení najdete v tématu [řešení pro systém Office zabezpečení](../vsto/securing-office-solutions.md).  
  
 Pro projekty na úrovni dokumentu musíte také přidat plně kvalifikované umístění dokumentu do seznamu důvěryhodných složky Office. Další informace najdete v tématu [udělit důvěryhodnost dokumenty](../vsto/granting-trust-to-documents.md).  
  
## <a name="change-the-platform-target"></a>Změnit cílová platforma  
 Ve výchozím nastavení, cílovou platformu v projektech pro systém Office je **jakýkoli procesor**. Obvykle byste neměli měnit tato nastavení. Řešení pro systém Office, které jsou vytvořeny tak, **jakýkoli procesor** Cílová platforma nastavení spuštění v 32bitové a 64bitové verze Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] nebo [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)].  
  
 Pouze v případě, že vytváříte řešení, které se spustí pouze v 64bitových verzích Microsoft, měli byste nastavit cílovou platformu pro x64 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] nebo [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)], a volá nativní rozhraní API 64-bit vašeho řešení. Další informace o změně nastavení cílové platformy naleznete v tématu [jak: Konfigurace projektů pro cílové platformy](../ide/how-to-configure-projects-to-target-platforms.md).  
  
 Pokud nastavíte Cílová platforma x64, řešení nespustí v 32bitové verze Windows nebo Office. X64 vyžaduje Cílová platforma řešení pro spouštění v 64bitového procesu.  
  
## <a name="use-the-clean-command"></a>Použití příkazu vyčistit  
 Odebrání souborů sestavením projektu z vývojového počítače, můžete použít **Vyčistit** příkaz **sestavení** v nabídce [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. **Vyčistit** příkaz odstraní všechny soubory v umístění výstupu sestavení. Pro projekty na úrovni aplikace **Vyčistit** příkaz také odebere položky registru, které jsou vytvořeny procesem sestavení.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Ladění projektů Office](../vsto/debugging-office-projects.md)|Uvede počet problémy při ladění projektů Office.|  
|[Návod: Vytvoření prvního přizpůsobení na úrovni dokumentu pro Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Ukazuje, jak vytvořit základní přizpůsobení úrovni dokumentu pro Excel.|  
|[Postupy: Opětovné povolení VSTO doplňku, který byl zakázán](../vsto/how-to-re-enable-a-vsto-add-in-that-has-been-disabled.md)|Popisuje, jak znovu povolit doplňku VSTO, který je pevně nebo obnovitelné zakázané.|  
|[Návrh a vytvoření řešení pro systém Office](../vsto/designing-and-creating-office-solutions.md)|Obsahuje odkazy na informace o vytváření řešení pro systém Office a o roli sestavení ve vašem řešení.|  
  
  