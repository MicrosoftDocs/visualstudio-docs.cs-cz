---
title: Kontextové parametry | Microsoft Docs
description: Seznamte se s parametry kontextu Visual Studio integrovaném vývojovém prostředí (IDE), které definují stav projektu při přidání nebo implementaci průvodce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 536e5abf92884c5c19399e73b4e1773e66919657
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898224"
---
# <a name="context-parameters"></a>Kontextové parametry
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaném vývojovém prostředí (IDE) můžete přidat průvodce do dialogových oken Nový projekt , **Přidat** novou položku nebo Přidat **dílčí** projekt. Přidaný průvodce je k dispozici v **nabídce Soubor** nebo kliknutím pravým tlačítkem na projekt **v Průzkumník řešení**. Integrované vývojové prostředí (IDE) předá implementaci průvodce kontextové parametry. Kontextové parametry definují stav projektu, když integrované vývojové prostředí volá průvodce.

 Integrované vývojové prostředí (IDE) spouští průvodce nastavením příznaku ve volání integrovaného vývojového prostředí <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> (IDE) na metodu pro projekt. Při nastavení musí projekt způsobit spuštění metody pomocí registrovaného názvu průvodce nebo identifikátoru GUID a dalších kontextových parametrů, které mu `IVsExtensibility::RunWizardFile` předá integrované vývojové prostředí (IDE).

## <a name="context-parameters-for-new-project"></a>Kontextové parametry pro nový projekt

| Parametr | Popis |
|-------------------------| - |
| `WizardType` | Zaregistrovaný typ průvodce ( <xref:EnvDTE.Constants.vsWizardNewProject> ) nebo identifikátor GUID, který označuje typ průvodce. V implementaci má průvodce identifikátor [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] GUID {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Řetězec, který je [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jedinečným názvem projektu. |
| `LocalDirectory` | Místní umístění pracovních souborů projektu. |
| `InstallationDirectory` | Cesta k adresáři [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je instalace. |
| `FExclusive` | Logický příznak, který označuje, že projekt by měl zavřít otevřená řešení. |
| `SolutionName` | Název souboru řešení bez části adresáře nebo *přípony .sln.* Název *souboru .suo* se vytvoří také pomocí `SolutionName` . Pokud tento argument není prázdný řetězec, průvodce použije před přidáním projektu <xref:EnvDTE._Solution.Create%2A> pomocí <xref:EnvDTE._Solution.AddFromTemplate%2A> . Pokud je tento název prázdný řetězec, použijte bez <xref:EnvDTE._Solution.AddFromTemplate%2A> volání <xref:EnvDTE._Solution.Create%2A> . |
| `Silent` | Logická hodnota, která určuje, jestli se má průvodce spustit bezobslužně, jako kdyby **se** klikli na Dokončit ( `TRUE` ). |

## <a name="context-parameters-for-add-new-item"></a>Kontextové parametry pro přidání nové položky

| Parametr | Popis |
|-------------------------| - |
| `WizardType` | Zaregistrovaný typ průvodce ( <xref:EnvDTE.Constants.vsWizardAddItem> ) nebo identifikátor GUID, který označuje typ průvodce. V implementaci má průvodce identifikátor [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] GUID {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Řetězec, který je [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jedinečným názvem projektu. |
| `ProjectItems` | Místní umístění, které obsahuje pracovní soubory projektu. |
| `ItemName` | Název položky, která se má přidat. Tento název je buď výchozí název souboru, nebo název souboru, který uživatel zadá v **dialogovém okně Přidat** položky. Název je založen na příznakech, které jsou nastavené v *souboru .vsdir.* Název může být hodnota null. |
| `InstallationDirectory` | Cesta k adresáři [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je instalace. |
| `Silent` | Logická hodnota, která určuje, jestli se má průvodce spustit bezobslužně, jako kdyby **se** klikli na Dokončit ( `TRUE` ). |

## <a name="context-parameters-for-add-sub-project"></a>Kontextové parametry pro přidání dílčího projektu

| Parametr | Popis |
|-------------------------| - |
| `WizardType` | Zaregistrovaný typ průvodce ( <xref:EnvDTE.Constants.vsWizardAddSubProject> ) nebo identifikátor GUID, který označuje typ průvodce. V implementaci má průvodce identifikátor [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] GUID {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Řetězec, který je [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jedinečným názvem projektu. |
| `ProjectItems` | Ukazatel na `ProjectItems` kolekci, ve které průvodce pracuje. Tento ukazatel se předá průvodci na základě výběru hierarchie projektu. Uživatel obvykle vybere složku, do které se má položka umístit, a potom zavolá dialogové okno **Přidat** položku projektu. |
| `LocalDirectory` | Místní umístění pracovních souborů projektu. |
| `ItemName` | Název položky, která se má přidat. Tento název je buď výchozí název souboru, nebo název souboru, který uživatel zadá v **dialogovém okně Přidat** položky. Název je založen na příznakech, které jsou nastavené v *souboru .vsdir.* Název může být hodnota null. |
| `InstallationDirectory` | Cesta k [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] adresáři instalace. |
| `Silent` | Logická hodnota, která určuje, jestli se má průvodce spustit bezobslužně, jako kdyby **se** klikli na Dokončit ( `TRUE` ). |

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Vlastní parametry](../../extensibility/internals/custom-parameters.md)
- [Průvodci](../../extensibility/internals/wizards.md)
- [Soubor průvodce (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Kontextové parametry pro spuštění průvodců](/previous-versions/tz690efs(v=vs.140))