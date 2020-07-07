---
title: Vytvoření balíčku řešení služby SharePoint pomocí úloh nástroje MSBuild
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c59a38e1153a57c1bd886121eeac244075045a42
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017016"
---
# <a name="how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks"></a>Postupy: vytvoření balíčku řešení služby SharePoint pomocí úloh nástroje MSBuild
  Můžete sestavit, vyčistit a ověřit balíček služby SharePoint (*. wsp*) pomocí úloh nástroje MSBuild příkazového řádku ve vývojovém počítači. Tyto příkazy lze použít také k automatizaci procesu sestavení pomocí Team Foundation Server v počítači sestavení.

## <a name="build-a-sharepoint-package"></a>Sestavení balíčku služby SharePoint

#### <a name="to-build-a-sharepoint-package"></a>Sestavení balíčku služby SharePoint

1. V nabídce **Start** systému Windows vyberte položku **všechny programy**  >  **Accessories**  >  **příkazový řádek**.

2. Přejděte do adresáře, kde se nachází váš projekt služby SharePoint.

3. Zadáním následujícího příkazu vytvořte balíček pro projekt. Nahraďte *ProjectFileName* názvem projektu.

    ```cmd
    msbuild /t:Package ProjectFileName
    ```

     Například můžete spustit jeden z následujících příkazů pro zabalení projektu služby SharePoint s názvem ListDefinition1.

    ```cmd
    msbuild /t:Package ListDefinition1.vbproj
    msbuild /t:Package ListDefinition1.csproj
    ```

## <a name="clean-a-sharepoint-package"></a>Vyčištění balíčku služby SharePoint

#### <a name="to-clean-a-sharepoint-package"></a>Vyčištění balíčku služby SharePoint

1. Otevřete okno příkazového řádku.

2. Přejděte do adresáře, kde se nachází váš projekt služby SharePoint.

3. Zadejte následující příkaz pro vyčištění balíčku pro projekt. Nahraďte *ProjectFileName* názvem projektu.

    ```cmd
    msbuild /t:CleanPackage ProjectFileName
    ```

     Například můžete spustit jeden z následujících příkazů k vyčištění projektu služby SharePoint s názvem ListDefinition1.

    ```cmd
    msbuild /t:CleanPackage ListDefinition1.vbproj
    msbuild /t:CleanPackage ListDefinition1.csproj
    ```

## <a name="validate-a-sharepoint-package"></a>Ověření balíčku služby SharePoint

#### <a name="to-validate-a-sharepoint-package"></a>Ověření balíčku služby SharePoint

1. Otevřete okno příkazového řádku.

2. Přejděte do adresáře, kde se nachází váš projekt služby SharePoint.

3. Zadejte následující příkaz pro ověření balíčku projektu. Nahraďte *ProjectFileName* názvem projektu.

    ```cmd
    msbuild /t:ValidatePackage ProjectFileName
    ```

     Například můžete spustit jeden z následujících příkazů pro ověření projektu služby SharePoint s názvem ListDefinition1.

    ```cmd
    msbuild /t:ValidatePackage ListDefinition1.vbproj
    msbuild /t:ValidatePackage ListDefinition1.csproj
    ```

## <a name="set-properties-in-a-sharepoint-package"></a>Nastavení vlastností v balíčku služby SharePoint

#### <a name="to-set-a-property-in-a-sharepoint-package"></a>Nastavení vlastnosti v balíčku služby SharePoint

1. Otevřete okno příkazového řádku.

2. Přejděte do adresáře, kde se nachází váš projekt služby SharePoint.

3. Zadejte následující příkaz pro nastavení vlastnosti v balíčku pro projekt. Nahraďte *PropertyName* vlastností, kterou chcete nastavit.

    ```cmd
    msbuild /property:PropertyName=Value
    ```

     Můžete například spustit následující příkaz, který nastaví úroveň upozornění.

    ```cmd
    msbuild /property:WarningLevel = 2
    ```

## <a name="see-also"></a>Viz také:
- [Vytvoření funkcí služby SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Postupy: přizpůsobení funkce služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [Postupy: přidávání a odebírání položek do funkcí služby SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
