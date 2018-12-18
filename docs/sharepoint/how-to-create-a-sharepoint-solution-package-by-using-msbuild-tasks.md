---
title: 'Postupy: vytvoření balíčku řešení služby SharePoint pomocí úloh nástroje MSBuild | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5a95eb80b860a1447fe6e958edb9c98b66805a90
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37120160"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Postupy: vytvoření balíčku řešení služby SharePoint pomocí úloh nástroje MSBuild
  Můžete vytvářet, vyčistit a ověřit balíček služby SharePoint (*WSP*) pomocí příkazového řádku úlohy nástroje MSBuild na vývojovém počítači. Můžete také používat tyto příkazy pro automatizaci procesu sestavení pomocí serveru Team Foundation Server na počítači sestavení.  
  
## <a name="build-a-sharepoint-package"></a>Vytvořit balíček služby SharePoint  
  
#### <a name="to-build-a-sharepoint-package"></a>Chcete-li vytvořit balíček služby SharePoint  
  
1.  V systému Windows **spustit** nabídce zvolte **všechny programy** > **Příslušenství** > **příkazového řádku**.  
  
2.  Přejděte do adresáře, kde se nachází projektu služby SharePoint.  
  
3.  Zadejte následující příkaz k vytvoření balíčku pro projekt. Nahraďte *ProjectFileName* s názvem projektu.  
  
    ```cmd  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Například můžete spustit jeden z následujících příkazů pro balíček názvem ListDefinition1 projektu služby SharePoint.  
  
    ```cmd  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## <a name="clean-a-sharepoint-package"></a>Vyčištění balíček služby SharePoint  
  
#### <a name="to-clean-a-sharepoint-package"></a>Pro čištění balíček služby SharePoint  
  
1.  Otevřete okno příkazového řádku.  
  
2.  Přejděte do adresáře, kde se nachází projektu služby SharePoint.  
  
3.  Zadejte následující příkaz k vyčištění balíčků pro projekt. Nahraďte *ProjectFileName* s názvem projektu.  
  
    ```cmd  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Například můžete spustit jeden z následujících příkazů pro čištění názvem ListDefinition1 projektu služby SharePoint.  
  
    ```cmd  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## <a name="validate-a-sharepoint-package"></a>Ověřit balíček služby SharePoint  
  
#### <a name="to-validate-a-sharepoint-package"></a>Chcete-li ověřit balíček služby SharePoint  
  
1.  Otevřete okno příkazového řádku.  
  
2.  Přejděte do adresáře, kde se nachází projektu služby SharePoint.  
  
3.  Zadejte následující příkaz k ověření balíčků pro projekt. Nahraďte *ProjectFileName* s názvem projektu.  
  
    ```cmd  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Například můžete spustit jeden z následujících příkazů pro ověření názvem ListDefinition1 projektu služby SharePoint.  
  
    ```cmd  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## <a name="set-properties-in-a-sharepoint-package"></a>Nastavit vlastnosti v balíčku služby SharePoint  
  
#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Chcete-li nastavit vlastnosti v balíčku služby SharePoint  
  
1.  Otevřete okno příkazového řádku.  
  
2.  Přejděte do adresáře, kde se nachází projektu služby SharePoint.  
  
3.  Zadejte následující příkaz pro nastavení vlastnosti v balíčku pro projekt. Nahraďte *PropertyName* s vlastností, které chcete nastavit.  
  
    ```cmd  
    msbuild /property:PropertyName=Value  
    ```  
  
     Můžete například spustit následující příkaz pro nastavení úroveň pro upozornění.  
  
    ```cmd  
    msbuild /property:WarningLevel = 2  
    ```  
  
## <a name="see-also"></a>Viz také:
 [Vytváření funkcí služby SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Postupy: přizpůsobení funkce služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Postupy: Přidání a odebrání položek z funkcí služby SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
