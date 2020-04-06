---
title: Parametry kontextu | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 6673ad8f26c94165635b5f1bc652b91dcbbfd24f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709307"
---
# <a name="context-parameters"></a>Kontextové parametry
V [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovaném vývojovém prostředí (IDE) můžete přidat průvodce do dialogových oken **Nový projekt**, **Přidat novou položku**nebo Přidat dílčí **projekt.** Přidávající průvodci jsou k dispozici v nabídce **Soubor** nebo klepnutím pravým tlačítkem myši na projekt v **Průzkumníku řešení**. Rozhraní IDE předá parametry kontextu implementaci průvodce. Parametry kontextu definují stav projektu, když rozhraní IDE volá průvodce.

 Rozhraní IDE spustí průvodce <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> nastavením příznaku ve volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> ide metody pro projekt. Při nastavení projektu musí `IVsExtensibility::RunWizardFile` způsobit, že metoda má být provedena pomocí názvu registrovaného průvodce nebo GUID a dalších parametrů kontextu, které mu rozhraní IDE předá.

## <a name="context-parameters-for-new-project"></a>Kontextové parametry pro nový projekt

| Parametr | Popis |
|-------------------------| - |
| `WizardType` | Registrovaný typ<xref:EnvDTE.Constants.vsWizardNewProject>průvodce ( ) nebo identifikátor GUID, který označuje typ průvodce. V [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementaci je identifikátor GUID pro průvodce {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Řetězec, který je [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jedinečný název projektu. |
| `LocalDirectory` | Místní umístění souborů pracovního projektu. |
| `InstallationDirectory` | Cesta k [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] adresáři je instalace. |
| `FExclusive` | Logický příznak, který označuje, že projekt by měl zavřít otevřená řešení. |
| `SolutionName` | Název souboru řešení bez části adresáře nebo přípony *.sln.* Název *souboru .suo* je `SolutionName`také vytvořen pomocí . Pokud tento argument není prázdný řetězec, <xref:EnvDTE._Solution.Create%2A> průvodce použije <xref:EnvDTE._Solution.AddFromTemplate%2A>před přidáním projektu s . Pokud je tento název prázdný <xref:EnvDTE._Solution.AddFromTemplate%2A> řetězec, použijte bez volání <xref:EnvDTE._Solution.Create%2A>. |
| `Silent` | Logická hodnota, která označuje, zda **Finish** má průvodce běžet`TRUE`tiše, jako by bylo kliknuto na dokončení ( ). |

## <a name="context-parameters-for-add-new-item"></a>Parametry kontextu pro přidat novou položku

| Parametr | Popis |
|-------------------------| - |
| `WizardType` | Registrovaný typ<xref:EnvDTE.Constants.vsWizardAddItem>průvodce ( ) nebo identifikátor GUID, který označuje typ průvodce. V [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementaci je identifikátor GUID pro průvodce {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Řetězec, který je [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jedinečný název projektu. |
| `ProjectItems` | Místní umístění, které obsahuje soubory pracovního projektu. |
| `ItemName` | Název položky, která má být přidána. Tento název je buď výchozí název souboru, nebo název souboru, který uživatel zadá z dialogového okna **Přidat položky.** Název je založen na příznaky, které jsou nastaveny v souboru *.vsdir.* Název může být nulová hodnota. |
| `InstallationDirectory` | Cesta k [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] adresáři je instalace. |
| `Silent` | Logická hodnota, která označuje, zda **Finish** má průvodce běžet`TRUE`tiše, jako by bylo kliknuto na dokončení ( ). |

## <a name="context-parameters-for-add-sub-project"></a>Parametry kontextu pro přidat dílčí projekt

| Parametr | Popis |
|-------------------------| - |
| `WizardType` | Registrovaný typ<xref:EnvDTE.Constants.vsWizardAddSubProject>průvodce ( ) nebo identifikátor GUID, který označuje typ průvodce. V [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] implementaci je identifikátor GUID pro průvodce {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}. |
| `ProjectName` | Řetězec, který je [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] jedinečný název projektu. |
| `ProjectItems` | Ukazatel na `ProjectItems` kolekci, na které průvodce pracuje. Tento ukazatel je předán průvodci na základě výběru hierarchie projektu. Uživatel obvykle vybere složku, do které chcete položku umístit, a potom zavolá dialogové okno **Přidat položku** projektu. |
| `LocalDirectory` | Místní umístění souborů pracovního projektu. |
| `ItemName` | Název položky, která má být přidána. Tento název je buď výchozí název souboru, nebo název souboru, který uživatel zadá z dialogového okna **Přidat položky.** Název je založen na příznaky, které jsou nastaveny v souboru *.vsdir.* Název může být nulová hodnota. |
| `InstallationDirectory` | Cesta k [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] adresáři instalace. |
| `Silent` | Logická hodnota, která označuje, zda **Finish** má průvodce běžet`TRUE`tiše, jako by bylo kliknuto na dokončení ( ). |

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [Vlastní parametry](../../extensibility/internals/custom-parameters.md)
- [Průvodci](../../extensibility/internals/wizards.md)
- [Soubor Průvodce (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
- [Parametry kontextu pro spouštění průvodců](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
