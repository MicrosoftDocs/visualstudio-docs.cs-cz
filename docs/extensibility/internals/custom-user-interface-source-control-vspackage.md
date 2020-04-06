---
title: Vlastní uživatelské rozhraní (správa zdrojového kódu VSPackage) | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interface, source control packages
- source control packages, user interface
ms.assetid: f35ddb24-53bf-461e-b34f-7414f657c082
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6ef807cef17a6ca3cddfee05ba57ace27e34a9e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708934"
---
# <a name="custom-user-interface-source-control-vspackage"></a>Vlastní uživatelské rozhraní (správa zdrojového kódu VSPackage)
A VSPackage deklaruje své položky nabídky a jejich výchozí stavy prostřednictvím souboru příkazu Visual Studio (*.vsct*). Integrované [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vývojové prostředí (IDE) zobrazí položky nabídky v jejich výchozí stavy, dokud vSPackage je načten. Následně <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> je metoda volána k povolení nebo zakázání položek nabídky.

 VSPackage můžete nastavit klíč registru, takže VSPackage lze automaticky načíst v závislosti na kontextu uživatelského rozhraní příkazu (UI), i když obvykle zdroj ovládacího prvku VSPackage by měl načíst na vyžádání namísto pouze přepnutí do určitého kontextu uživatelského rozhraní. Další informace o klíči registru **AutoLoadPackages** naleznete v [tématu Správa balíčků VSPackages](../../extensibility/managing-vspackages.md).

## <a name="vspackage-ui"></a>VSPackage UI
 Balíček správy zdrojového kódu je implementován jako VSPackage a nepoužívá žádné ui z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Každý zdrojový prvek VSPackage musí zadat své vlastní prvky uživatelského rozhraní, jako jsou položky nabídky, skupiny nabídek, okna nástrojů, panely nástrojů a všechny požadované uživatelské rozhraní pro nastavení možností specifických pro zdrojového ovládacího prvku VSPackage. Tyto prvky uživatelského rozhraní lze povolit staticky nebo dynamicky. Statické prvky uživatelského rozhraní jsou definovány v souboru *.vsct* a jsou zobrazeny bez ohledu na to, zda je balíček VSPackage načten či nikoli. Dynamické prvky uživatelského rozhraní mohou být viditelné v <xref:EnvDTE.Constants.vsContextNoSolution>závislosti na kontextu určitého uživatelského rozhraní příkazu, například , nebo jako výsledek volání <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody. Viditelnost dynamických prvků uživatelského rozhraní je v souladu se strategií pro zpožděné načítání VSPackages.

## <a name="ui-constraints-on-source-control-vspackages"></a>Omezení u ina na zdrojové správě VSPackages
 Vzhledem k tomu, že zdrojový ovládací prvek VSPackage nelze odebrat z ide po jeho načtení, VSPackage musí být schopen zadat neaktivní stav. Když VSPackage obdrží oznámení, že již není aktivní, VSPackage zakáže jeho uznané a ignoruje všechny externí ide interakce. VSPackage implementace <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody by měl skrýt příkazy, pokud VSPackage není aktivní.

 Každý zdrojový prvek VSPackage `IVsSccProvider` musí implementovat rozhraní. Dvě metody na <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetActive%2A> rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider.SetInactive%2A>a , musí být implementovány VSPackage.

 Zdroj ovládacího prvku VSPackage může mít přihlášeni k odběru <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>různých událostí ide, které jsou implementovány , a tak dále. VSPackage také může mít implementovány registry povoleno rozhraní pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>zpětné volání, jako je například . Tato rozhraní musí být ignorovány, pokud nejsou aktivní.

 V následujícím seznamu jsou uvedena rozhraní ovlivněná aktivním stavem správy zdrojového kódu VSPackage:

- Sledování událostí dokumentů projektu.

- Události řešení.

- Rozhraní perzistence řešení. Pokud jsou balíčky neaktivní, neměly by zapisovat do souborů *.sln* a *.suo.*

- Zařízení prorozšíření vlastností.

  Povinné <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, a také všechny volitelné rozhraní přidružené ke sněmu zdrojového kódu nejsou volány, pokud je neaktivní ovládací prvek zdroj Ového kódu VSPackage.

  Při [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] spuštění ide [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nastaví kontext příkazu ui na ID aktuální výchozí ovládací prvek zdrojOvého kódu VSPackage ID. To způsobí, že statické ui aktivní správy zdrojového kódu VSPackage se zobrazí v ide bez skutečného načtení VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]pozastaví pro VSPackage zaregistrovat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider> se prostřednictvím před provede volání VSPackage.

  Následující tabulka popisuje konkrétní podrobnosti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o tom, jak ide skryje různé položky ui.

| Položka uj. | Popis |
| - | - |
| Nabídky a panely nástrojů | Balíček správy zdrojového kódu musí nastavit počáteční stavy viditelnosti nabídky a panelu nástrojů na ID balíčku správy zdrojového kódu v části [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) souboru *.vsct.* To umožňuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ide nastavit stav položek nabídky vhodně bez načtení VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> a volání implementace metody. |
| Okna nástrojů | Zdrojový prvek VSPackage skryje všechna okna nástrojů, která vlastní, když je neaktivní. |
| Stránky možností specifické pro ovládací prvek VSPackage | Klíč registru **HKLM\SOFTWARE\Microsoft\VisualStudio\X.Y\ToolsOptionsPages\VisibilityCmdUIContexts** umožňuje vspackage nastavit kontexty, ve kterých vyžaduje, aby jeho možnosti stránky, které mají být zobrazeny. Položka registru pod tímto klíčem by musela být vytvořena pomocí ID služby (SID) služby správy zdrojového kódu a přiřazením hodnoty DWORD 1. Vždy, když dojde k události ui v kontextu správy zdrojového kódu VSPackage je registrována, Bude VSPackage volána, pokud je aktivní. |

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterScciProvider>
- <xref:EnvDTE.Constants.vsContextNoSolution>
- [Správa balíčků VSPackage](../../extensibility/managing-vspackages.md)
