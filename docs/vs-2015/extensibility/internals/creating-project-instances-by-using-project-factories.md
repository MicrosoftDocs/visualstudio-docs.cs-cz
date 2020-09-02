---
title: Vytváření instancí projektu pomocí Továrnování projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f26b11aaf74b73535c82ebcd6422f3be0bba3f22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697206"
---
# <a name="creating-project-instances-by-using-project-factories"></a>Vytváření instancí projektu pomocí objektů pro vytváření projektů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Typy projektů v aplikaci [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] používají *objekt* pro vytváření projektů k vytvoření instancí objektů projektu. Objekt pro vytváření projektu je podobný jako objekt pro vytváření standardních tříd pro spoluvytvořitelné objekty COM. Objekty projektu však nelze vytvořit, ale lze je vytvořit pouze pomocí objektu pro vytváření projektu.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Rozhraní IDE volá objekt pro vytváření projektu implementovaný ve VSPackage, když uživatel načte existující projekt nebo vytvoří nový projekt v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Nový objekt projektu poskytuje integrované vývojové prostředí (IDE) s dostatečnými informacemi k naplnění Průzkumník řešení. Nový objekt projektu také poskytuje požadovaná rozhraní pro podporu všech relevantních akcí uživatelského rozhraní iniciované rozhraním IDE.  
  
 Rozhraní můžete implementovat <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> ve třídě v projektu. Obvykle se nachází ve vlastním modulu.  
  
 Příklad implementace `IVsProjectFactory` rozhraní naleznete v tématu PrjFac. cpp, který je obsažen v adresáři [Basic Project](https://msdn.microsoft.com/385fd2a3-d9f1-4808-87c2-a3f05a91fc36) Sample.  
  
 Projekty, které podporují agregaci vlastníkem, musí v souboru projektu zachovat klíč vlastníka. Pokud <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> je metoda volána na projektu s klíčem vlastníka, pak vlastněný projekt převede svůj klíč vlastníka na GUID objektu pro vytváření projektu a pak zavolá `CreateProject` metodu v tomto objektu pro vytváření projektu, aby provedla skutečné vytvoření.  
  
## <a name="creating-an-owned-project"></a>Vytváření vlastněných projektů  
 Vlastník vytvoří vlastněný projekt ve dvou fázích:  
  
1. Voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A> metody. To dává vlastněné projektu možnost vytvořit agregovaný objekt projektu na základě řízení vstupu `IUnknown` . Vlastněný projekt předá vnitřní `IUnknown` a agregovaný objekt zpět k nadřazenému projektu. To dává vlastněné projektu možnost Uložit vnitřní `IUnknown` .  
  
2. Voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A> metody. Vlastněný projekt provede všechny své instance, pokud je tato metoda volána namísto volání `IVsProjectFactory::CreateProject` jako by to byl případ pro projekty, které nejsou vlastněny. Vstupní `VSOWNEDPROJECTOBJECT` výčet je obvykle agregovaný vlastněný projekt. Vlastněný projekt může tuto proměnnou použít k určení, zda byl jeho objekt projektu již vytvořen (soubor cookie se nerovná hodnotě NULL) nebo musí být vytvořen (soubor cookie se rovná NULL).  
  
   Typy projektů jsou identifikovány jedinečným identifikátorem GUID projektu, podobně jako CLSID objektu COM. Jeden objekt pro vytváření projektu obvykle zpracovává instance jednoho typu projektu, i když je možné mít jeden objekt pro vytváření projektu více než jeden identifikátor GUID typu projektu.  
  
   Typy projektů jsou přidruženy k určité příponě názvu souboru. Když se uživatel pokusí otevřít existující soubor projektu nebo se pokusí vytvořit nový projekt naklonování šablony, rozhraní IDE použije rozšíření na soubor k určení odpovídajícího identifikátoru GUID projektu.  
  
   Jakmile rozhraní IDE určí, zda musí vytvořit nový projekt nebo otevřít existující projekt určitého typu, rozhraní IDE použije informace v systémovém registru v oddílu [HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio\8.0\Projects] k nalezení, který VSPackage implementuje požadovaný objekt pro vytváření projektu. Rozhraní IDE načte tento VSPackage. V <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> metodě musí VSPackage registrovat svůj objekt pro vytváření projektu pomocí rozhraní IDE voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A> metody.  
  
   Primární metodou `IVsProjectFactory` rozhraní je <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> , že by měla zpracovávat dva scénáře: otevření existujícího projektu a vytvoření nového projektu. Většina projektů ukládá svůj stav projektu do souboru projektu. Nové projekty jsou obvykle vytvořeny vytvořením kopie souboru šablony předaného do `CreateProject` metody a následným otevřením kopie. Existující projekty jsou vytvořeny přímo otevřením souboru projektu předaného `CreateProject` metodě. `CreateProject`Metoda může uživateli podle potřeby zobrazit další funkce uživatelského rozhraní.  
  
   Projekt může také použít žádné soubory a místo toho uložit stav projektu v jiném úložném mechanismu než v systému souborů, jako je například databáze nebo webový server. V tomto případě parametr názvu souboru předaný `CreateProject` metodě není ve skutečnosti cestou systému souborů, ale jedinečným řetězcem, který identifikuje data projektu. Nemusíte kopírovat soubory šablon, které jsou předány, `CreateProject` aby se aktivovala příslušná sekvence konstrukce, která se má spustit.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [Kontrolní seznam: Vytvoření nových typů projektů](../../extensibility/internals/checklist-creating-new-project-types.md)
