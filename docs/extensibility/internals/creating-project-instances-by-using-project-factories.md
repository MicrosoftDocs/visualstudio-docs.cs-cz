---
title: Vytváření instancí projektu pomocí továren projektu | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31ba5dd11af18f8a723b2271544eff2bd292e2e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709053"
---
# <a name="create-project-instances-by-using-project-factories"></a>Vytvoření instancí projektu pomocí továren projektu
Typy projektů [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] používají *továrnu projektu* k vytvoření instancí objektů projektu. Továrna projektu je podobná standardní třídy factory pro cocreatable com objekty. Objekty projektu však nejsou cocreatable; lze vytvořit pouze pomocí továrny projektu.

 IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] volá továrnu projektu implementované v Balíčku VSPackage, když uživatel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]načte existující projekt nebo vytvoří nový projekt v aplikaci . Nový objekt projektu poskytuje rozhraní IDE dostatek informací k naplnění **Průzkumníka řešení**. Nový objekt projektu také poskytuje požadovaná rozhraní pro podporu všech příslušných akcí uživatelského rozhraní iniciovaných rozhraním IDE.

 Rozhraní můžete <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> implementovat ve třídě v projektu. Obvykle se nachází ve vlastním modulu.

 Projekty, které podporují agregaci vlastníkem musí zachovat klíč vlastníka v souboru projektu. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> je metoda volána na projekt s klíčem vlastníka, vlastněný projekt převede svůj `CreateProject` klíč vlastníka na identifikátor GUID továrny projektu a poté zavolá metodu v této továrně projektu k vytvoření skutečného vytvoření.

## <a name="create-an-owned-project"></a>Vytvoření vlastněného projektu
 Vlastník vytvoří vlastněný projekt ve dvou fázích:

1. Voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> metody. To dává vlastněný projekt možnost vytvořit agregovaný objekt `IUnknown`projektu na základě vstupní řízení . Vlastněný projekt předá `IUnknown` vnitřní a agregovaný objekt zpět do projektu vlastníka. To dává vlastněný projekt možnost `IUnknown`uložit vnitřní .

2. Voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> metody. Vlastněný projekt provede všechny jeho konkretizovat, `IVsProjectFactory::CreateProject` když je tato metoda volána namísto volání, jak by tomu bylo v případě projektů, které nejsou vlastněny. Vstupní `VSOWNEDPROJECTOBJECT` výčet je obvykle agregovaný vlastněný projekt. Vlastněný projekt může tuto proměnnou použít k určení, zda byl jeho objekt projektu již vytvořen (soubor cookie se nerovná hodnotě NULL) nebo musí být vytvořen (soubor cookie se rovná hodnotě NULL).

   Typy projektů jsou identifikovány jedinečným identifikátorem GUID projektu, podobně jako identifikátor CLSID cocreatable COM objektu. Obvykle jeden projekt factory zpracovává vytváření instancí jednoho typu projektu, i když je možné mít jeden projekt factory popisovat více než jeden typ projektu GUID.

   Typy projektů jsou přidruženy k určité příponě názvu souboru. Když se uživatel pokusí otevřít existující soubor projektu nebo se pokusí vytvořit nový projekt klonováním šablony, ide používá příponu v souboru k určení odpovídajícího identifikátoru GUID projektu.

   Jakmile rozhraní IDE určí, zda musí vytvořit nový projekt nebo otevřít existující projekt určitého typu, použije ide informace v systémovém registru pod **[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects]** k určení, který vSPackage implementuje požadovanou továrnu projektu. IDE načte tento VSPackage. V <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodě VSPackage musí zaregistrovat své továrny projektu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> s IDE voláním metody.

   Primární metoda `IVsProjectFactory` rozhraní je <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>, který by měl zpracovat dva scénáře: otevření existujícího projektu a vytvoření nového projektu. Většina projektů ukládá svůj stav projektu do souboru projektu. Obvykle nové projekty jsou vytvořeny vytvořením kopie souboru `CreateProject` šablony předány metodě a potom otevření kopie. Existující projekty jsou vytvořena instance přímým otevřením `CreateProject` souboru projektu předán metodě. Metoda `CreateProject` může zobrazit další funkce uživatelského rozhraní pro uživatele podle potřeby.

   Projekt může také použít žádné soubory a místo toho uložit svůj stav projektu v mechanismu úložiště než v systému souborů, jako je například databáze nebo webový server. V tomto případě parametr název souboru předaný metodě `CreateProject` není ve skutečnosti cestou systému souborů, ale jedinečným řetězcem – adresou URL – k identifikaci dat projektu. Není nutné kopírovat soubory šablony, které `CreateProject` jsou předány k aktivaci příslušné konstrukční sekvence, která má být provedena.

## <a name="see-also"></a>Viz také
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>
- [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
