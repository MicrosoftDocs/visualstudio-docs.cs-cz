---
title: Vlastní uživatelské rozhraní (VSPackage správy zdrojového kódu) | Microsoft Docs
description: Naučte se, jak vytvořit vlastní uživatelské rozhraní (UI) v aplikaci Visual Studio pomocí sady VSPackage správy zdrojového kódu pro určení prvků uživatelského rozhraní.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1239b11e814ba08e4e481358f5e7fdd0e5dc666b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091029"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Vlastní uživatelské rozhraní (VSPackage správy zdrojového kódu)
VSPackage deklaruje své položky nabídky a jejich výchozí stavy prostřednictvím souboru tabulky příkazů sady Visual Studio (*. vsct*). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Integrované vývojové prostředí (IDE) zobrazuje položky nabídky ve svých výchozích stavech, dokud není načteno VSPackage. Následně <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> je metoda volána k povolení nebo zakázání položek nabídky.

 Sada VSPackage může nastavit klíč registru, aby VSPackage mohl být automaticky načten v závislosti na kontextu uživatelského rozhraní příkazu (UI), přestože obvykle by měl být v rámci správy zdrojového kódu místo pouhého přepnutí do konkrétního uživatelského rozhraní zaveden na vyžádání. Další informace o klíči registru **AutoLoadPackages** najdete v tématu [Správa VSPackage](../../extensibility/managing-vspackages.md).

## <a name="vspackage-ui"></a>ROZHRANÍ VSPackage
 Balíček správy zdrojového kódu je implementován jako VSPackage a nepoužívá žádné uživatelské rozhraní z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Každý prvek VSPackage správy zdrojového kódu musí určovat své vlastní prvky uživatelského rozhraní, jako jsou položky nabídky, skupiny nabídek, okna nástrojů, panely nástrojů a libovolné požadované uživatelské rozhraní pro nastavení možností určených pro VSPackage správy zdrojového kódu. Tyto prvky uživatelského rozhraní lze povolit staticky nebo dynamicky. Statické prvky uživatelského rozhraní jsou definovány v souboru *. vsct* a jsou zobrazeny, zda je rozhraní VSPackage načteno nebo ne. Dynamické prvky uživatelského rozhraní mohou být viditelné v závislosti na konkrétním kontextu uživatelského rozhraní, jako je například <xref:EnvDTE.Constants.vsContextNoSolution> nebo jako výsledek volání <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody. Viditelnost dynamických prvků uživatelského rozhraní odpovídá strategii pro opožděné načítání VSPackage.

## <a name="ui-constraints-on-source-control-vspackages"></a>Omezení uživatelského rozhraní pro VSPackage správy zdrojového kódu
 Protože VSPackage správy zdrojového kódu nelze odebrat z rozhraní IDE po jeho načtení, musí být VSPackage schopen zadat neaktivní stav. Když VSPackage obdrží oznámení, že již není aktivní, VSPackage zakáže své uživatelské rozhraní a ignoruje všechny externí interakce IDE. Implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody VSPackage by měla skrýt příkazy, pokud není aktivní rozhraní VSPackage.

 Každý prvek VSPackage správy zdrojového kódu musí implementovat `IVsSccProvider` rozhraní. Dvě metody rozhraní, <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A> , musí být implementovány pomocí VSPackage.

 Rozhraní VSPackage správy zdrojového kódu se může přihlásit k odběru různých událostí IDE, které jsou implementované pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> a tak dále. VSPackage také mohl implementovat rozhraní zpětného volání s povoleným registrem, jako je například <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> . Tato rozhraní musí být všechna ignorována, pokud jsou neaktivní.

 Následující seznam uvádí rozhraní ovlivněná aktivním stavem balíčku VSPackage správy zdrojového kódu:

- Sledujte události dokumentů projektu.

- Události řešení.

- Rozhraní trvalosti řešení. Pokud je neaktivní, balíčky by neměly zapisovat do souborů *. sln* a *. suo* .

- Rozšířené vlastnosti.

  Požadovaná <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> a a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> také všechna volitelná rozhraní přidružená ke správě zdrojového kódu nejsou volána, když je prvek VSPackage správy zdrojového kódu neaktivní.

  Po [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] spuštění rozhraní IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nastaví kontext uživatelského rozhraní příkazu na ID aktuálního výchozího ID balíčku VSPackage správy zdrojového kódu. To způsobí, že se statické uživatelské rozhraní sady VSPackage aktivního ovládacího prvku pro správu zdrojového kódu zobrazí v integrovaném vývojovém prostředí, aniž by bylo nutné načítat VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pozastaví, aby se VSPackage zaregistroval s [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] přes, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> než provede jakékoli volání VSPackage.

  Následující tabulka popisuje konkrétní podrobnosti o tom, jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rozhraní IDE skrývá jiné položky uživatelského rozhraní.

| Položka uživatelského rozhraní | Description |
| - | - |
| Nabídky a panely nástrojů | Balíček správy zdrojového kódu musí nastavit počáteční nabídku a stavy viditelnosti panelu nástrojů na ID balíčku správy zdrojového kódu v souboru *. vsct* v oddílu [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) . To umožňuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrovanému vývojovém prostředí (IDE) nastavit stav položek nabídky odpovídajícím způsobem bez načtení VSPackage a volání implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody. |
| Okna nástrojů | Rozhraní VSPackage správy zdrojového kódu skryje všechna okna nástrojů, která vlastní, když se nestane neaktivní. |
| Stránky možností specifické pro správu zdrojového kódu | Klíč registru **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts** umožňuje VSPackage nastavit kontexty, ve kterých se vyžaduje zobrazení stránek možností. Položka registru v rámci tohoto klíče by se musela vytvořit pomocí ID služby (SID) služby správy zdrojového kódu a přiřadit ji k hodnotě DWORD 1. Pokaždé, když dojde k události uživatelského rozhraní v kontextu, ve kterém je prvek VSPackage správy zdrojového kódu zaregistrován, rozhraní VSPackage bude voláno, pokud je aktivní. |

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Správa balíčků VSPackage](../../extensibility/managing-vspackages.md)
