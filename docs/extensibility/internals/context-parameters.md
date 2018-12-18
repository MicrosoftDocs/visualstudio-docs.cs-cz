---
title: Kontextové parametry | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d595bcc99cbacabd55c8e85775e1d691e917a41c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875837"
---
# <a name="context-parameters"></a>Kontextové parametry
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrované vývojové prostředí (IDE), můžete přidat průvodce, kteří **nový projekt**, **přidat novou položku**, nebo **přidat dílčí projekt** dialogových oknech. Přidání průvodců jsou k dispozici na **souboru** nabídek nebo kliknutím pravým tlačítkem myši projekt v **Průzkumníka řešení**. Integrovaného vývojového prostředí předá parametr kontextu pro implementaci průvodce. Kontextové parametry definovat stav projektu při integrovaném vývojovém prostředí volá průvodce.  
  
 Spuštění rozhraní IDE Průvodce nastavením <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> příznak při volání funkce rozhraní IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metodu pro projekt. Pokud nastavíte, projekt musíte zajistit, aby `IVsExtensibility::RunWizardFile` má být spuštěna s použitím Průvodce registrovaný název nebo identifikátor GUID a další kontextové parametry, které se předá rozhraní IDE.  
  
## <a name="context-parameters-for-new-project"></a>Kontextové parametry pro nový projekt  
  
| Parametr | Popis |
|-------------------------| - |
| `WizardType` | Registrovaný typ průvodce (<xref:EnvDTE.Constants.vsWizardNewProject>) nebo identifikátor GUID, který určuje typ průvodce. V [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] je implementace, identifikátor GUID pro Průvodce {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Řetězec, který je jedinečný [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] název projektu. |
| `LocalDirectory` | Místní umístění pracovní soubory projektu. |
| `InstallationDirectory` | Cestu k adresáři [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je instalace. |
| `FExclusive` | Logický příznak, který označuje, že by se měla zavřít projekt otevřete řešení. |
| `SolutionName` | Název souboru řešení bez část adresáře nebo *.sln* rozšíření. *.Suo* název souboru je také vytvořen pomocí `SolutionName`. Pokud tento argument není prázdný řetězec, použije průvodce <xref:EnvDTE._Solution.Create%2A> před přidáním projektu pomocí <xref:EnvDTE._Solution.AddFromTemplate%2A>. Pokud tento název je prázdný řetězec, použijte <xref:EnvDTE._Solution.AddFromTemplate%2A> bez volání <xref:EnvDTE._Solution.Create%2A>. |
| `Silent` | Logická hodnota, která označuje, zda by průvodce měl běžet tiše jakoby **Dokončit** bylo kliknuto (`TRUE`). |
  
## <a name="context-parameters-for-add-new-item"></a>Kontextové parametry pro přidání nové položky  
  
| Parametr | Popis |
|-------------------------| - |
| `WizardType` | Registrovaný typ průvodce (<xref:EnvDTE.Constants.vsWizardAddItem>) nebo identifikátor GUID, který určuje typ průvodce. V [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] je implementace, identifikátor GUID pro Průvodce {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Řetězec, který je jedinečný [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] název projektu. |
| `ProjectItems` | Místní umístění, které obsahuje pracovní soubory projektu. |
| `ItemName` | Název položky, která se má přidat. Tento název je výchozí název souboru nebo název souboru, který uživatel zadá z **přidat položky** dialogové okno. Název je založen na příznaky, které jsou nastaveny *.vsdir* souboru. Název může obsahovat hodnotu null. |
| `InstallationDirectory` | Cestu k adresáři [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je instalace. |
| `Silent` | Logická hodnota, která označuje, zda by průvodce měl běžet tiše jakoby **Dokončit** bylo kliknuto (`TRUE`). |
  
## <a name="context-parameters-for-add-sub-project"></a>Kontextové parametry pro přidání dílčí projekt  
  
| Parametr | Popis |
|-------------------------| - |
| `WizardType` | Registrovaný typ průvodce (<xref:EnvDTE.Constants.vsWizardAddSubProject>) nebo identifikátor GUID, který určuje typ průvodce. V [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] je implementace, identifikátor GUID pro Průvodce {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Řetězec, který je jedinečný [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] název projektu. |
| `ProjectItems` | Ukazatel `ProjectItems` kolekce, ve kterém funguje průvodce. Tento ukazatel je předán na základě výběru hierarchie projektu průvodce. Uživatel vybere obvykle složku, do které chcete vložit položky a pak zavolá projektu **přidat položku** dialogové okno. |
| `LocalDirectory` | Místní umístění pracovní soubory projektu. |
| `ItemName` | Název položky, která se má přidat. Tento název je výchozí název souboru nebo název souboru, který uživatel zadá z **přidat položky** dialogové okno. Název je založen na příznaky, které jsou nastaveny *.vsdir* souboru. Název může obsahovat hodnotu null. |
| `InstallationDirectory` | Cestu k adresáři [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instalace. |
| `Silent` | Logická hodnota, která označuje, zda by průvodce měl běžet tiše jakoby **Dokončit** bylo kliknuto (`TRUE`). |
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [Vlastní parametry](../../extensibility/internals/custom-parameters.md)   
 [Průvodce](../../extensibility/internals/wizards.md)   
 [Soubor průvodce (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [Kontextové parametry pro spouštění průvodců](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)