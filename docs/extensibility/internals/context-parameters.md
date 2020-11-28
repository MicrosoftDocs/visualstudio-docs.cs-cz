---
title: Kontextové parametry | Microsoft Docs
description: Přečtěte si o kontextových parametrech v integrovaném vývojovém prostředí (IDE) sady Visual Studio, které definuje stav projektu při přidání nebo implementaci průvodce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 654ebf68efebaa44766079c172e87396134805e3
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304715"
---
# <a name="context-parameters"></a>Kontextové parametry
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaném vývojovém prostředí (IDE) můžete přidat průvodce do dialogového okna **Nový projekt**, **Přidat novou položku** nebo **Přidat dílčí projekt** . Přidaní průvodci jsou k dispozici v nabídce **soubor** nebo kliknutím pravým tlačítkem myši na projekt v **Průzkumník řešení**. Rozhraní IDE předá parametry kontextu implementaci průvodce. Kontextové parametry definují stav projektu, když rozhraní IDE zavolá průvodce.

 Rozhraní IDE spustí Průvodce nastavením <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> příznaku v volání rozhraní IDE do <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metody pro projekt. Při nastavení musí projekt způsobit `IVsExtensibility::RunWizardFile` spuštění metody pomocí registrovaného názvu průvodce nebo identifikátoru GUID a dalších kontextových parametrů, které do něj rozhraní IDE předává.

## <a name="context-parameters-for-new-project"></a>Kontextové parametry pro nový projekt

| Parametr | Popis |
|-------------------------| - |
| `WizardType` | Registrovaný typ průvodce ( <xref:EnvDTE.Constants.vsWizardNewProject> ) nebo identifikátor GUID, který označuje typ průvodce. V [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementaci je identifikátor GUID pro Průvodce {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Řetězec, který je jedinečný [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] název projektu. |
| `LocalDirectory` | Místní umístění pracovních souborů projektu. |
| `InstallationDirectory` | Cesta k adresáři [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je instalace. |
| `FExclusive` | Logický příznak, který označuje, že by měl projekt zavřít otevřená řešení. |
| `SolutionName` | Název souboru řešení bez části adresáře nebo rozšíření *. sln* Název souboru *. suo* je také vytvořen pomocí `SolutionName` . Pokud tento argument není prázdným řetězcem, průvodce použije <xref:EnvDTE._Solution.Create%2A> před přidáním projektu s <xref:EnvDTE._Solution.AddFromTemplate%2A> . Pokud je tento název prázdným řetězcem, použijte <xref:EnvDTE._Solution.AddFromTemplate%2A> bez volání <xref:EnvDTE._Solution.Create%2A> . |
| `Silent` | Logická hodnota, která označuje, zda má být průvodce spuštěn tiše jako při kliknutí na tlačítko **Dokončit** `TRUE` . |

## <a name="context-parameters-for-add-new-item"></a>Kontextové parametry pro přidání nové položky

| Parametr | Popis |
|-------------------------| - |
| `WizardType` | Registrovaný typ průvodce ( <xref:EnvDTE.Constants.vsWizardAddItem> ) nebo identifikátor GUID, který označuje typ průvodce. V [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementaci je identifikátor GUID pro Průvodce {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Řetězec, který je jedinečný [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] název projektu. |
| `ProjectItems` | Místní umístění, které obsahuje pracovní soubory projektu. |
| `ItemName` | Název položky, která se má přidat Tento název je buď výchozím názvem souboru, nebo názvem souboru, který uživatel používá v dialogovém okně **Přidat položky** . Název je založen na příznacích, které jsou nastaveny v souboru *. vsdir* . Název může být hodnota null. |
| `InstallationDirectory` | Cesta k adresáři [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] je instalace. |
| `Silent` | Logická hodnota, která označuje, zda má být průvodce spuštěn tiše jako při kliknutí na tlačítko **Dokončit** `TRUE` . |

## <a name="context-parameters-for-add-sub-project"></a>Kontextové parametry pro přidat dílčí projekt

| Parametr | Popis |
|-------------------------| - |
| `WizardType` | Registrovaný typ průvodce ( <xref:EnvDTE.Constants.vsWizardAddSubProject> ) nebo identifikátor GUID, který označuje typ průvodce. V [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementaci je identifikátor GUID pro Průvodce {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Řetězec, který je jedinečný [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] název projektu. |
| `ProjectItems` | Ukazatel na `ProjectItems` kolekci, na které Průvodce pracuje. Tento ukazatel se předává průvodci na základě výběru hierarchie projektu. Uživatel obvykle vybere složku, do které chcete položku vložit, a potom zavolá dialogové okno **Přidat položku** projektu. |
| `LocalDirectory` | Místní umístění pracovních souborů projektu. |
| `ItemName` | Název položky, která se má přidat Tento název je buď výchozím názvem souboru, nebo názvem souboru, který uživatel používá v dialogovém okně **Přidat položky** . Název je založen na příznacích, které jsou nastaveny v souboru *. vsdir* . Název může být hodnota null. |
| `InstallationDirectory` | Cesta k adresáři [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instalace |
| `Silent` | Logická hodnota, která označuje, zda má být průvodce spuštěn tiše jako při kliknutí na tlačítko **Dokončit** `TRUE` . |

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Vlastní parametry](../../extensibility/internals/custom-parameters.md)
- [Průvodci](../../extensibility/internals/wizards.md)
- [Soubor průvodce (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Kontextové parametry pro spouštění průvodců](/previous-versions/tz690efs(v=vs.140))