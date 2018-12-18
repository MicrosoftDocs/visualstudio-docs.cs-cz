---
title: Parametr spolupracujícího sestavení sady Visual Studio zařazování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: douge
ms.openlocfilehash: e18667adb48f565f73acc14f5012f9c96283efe9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195011"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Parametr spolupracujícího sestavení sady Visual Studio zařazování
Volání nebo volat nespravovaný kód com. pravděpodobně rozšíření VSPackages, která jsou napsána ve spravovaném kódu. Argumenty metody jsou obvykle, transformovat nebo zařadit automaticky interoperační zařazovač. Ale někdy argumenty nelze transformovat v přímočarým způsobem. V těchto případech parametry prototyp metody sestavení vzájemné spolupráce se používají tak, aby odpovídaly parametrům funkcí modelu COM co nejpřesněji. Další informace najdete v tématu [zařazování Interop](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Obecná doporučení  
  
##### <a name="read-the-reference-documentation"></a>Přečtěte si referenční dokumentaci  
 Účinný způsob, jak detekovat problémy s interoperabilitou je, přečtěte si referenční dokumentaci pro jednotlivé metody.  
  
 Referenční dokumentace pro jednotlivé metody obsahuje tři relevantní části:  
  
-   [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] Prototyp funkce modelu COM.  
  
-   Metoda prototypu definiční sestavení.  
  
-   Seznam parametrů COM a krátký popis každého.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>Vyhledejte rozdíly mezi dvěma prototypů  
 Většina problémy s interoperabilitou odvozovat neshody mezi definice rozhraní COM určitého typu a stejného typu v definici [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sestavení vzájemné spolupráce. Představte si třeba rozdíl v možnost předávání `null` hodnotu v parametr [out]. Musíte hledat rozdíly mezi dva prototypy a vezměte v úvahu jejich důsledky pro data předávána.  
  
##### <a name="read-the-parameter-definitions"></a>Číst definice parametru  
 Číst definice parametru. COM je méně striktní než common language runtime (CLR) o kombinování různých typů dat v jeden parametr. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Rozhraní modelu COM využívat všech výhod této flexibility. Žádné parametry, které můžete předat nebo vyžadují nestandardní hodnoty nebo typ dat, jako je konstantní hodnota v parametru ukazatel, by jako takové popsané v dokumentaci.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>Objekty IUnknown předány jako typ void **  
 Vyhledejte [out] Parametry, které jsou definovány jako typ `void **` v modelu COM rozhraní, ale které jsou definovány jako `[``iid_is``]` v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototyp metody sestavení vzájemné spolupráce.  
  
 V některých případech vygeneruje rozhraní modelu COM `IUnknown` objektu a rozhraní modelu COM pak ji předá jako typ. `void **`. Tato rozhraní jsou obzvláště důležité, protože pokud je proměnná definovaná jako [out] v IDL, pak bude `IUnknown` objekt je referenčně s `AddRef` metody. Nevracení paměti dochází, pokud objekt není správně zpracovat.  
  
> [!NOTE]
>  `IUnknown` Objekt vytvořený rozhraní COM a vrátil [out] proměnné způsobí nevracení paměti, pokud není explicitně uvolněna.  
  
 Spravované metody, které zpracovávají tyto objekty by měly zpracovávat <xref:System.IntPtr> jako ukazatel na `IUnknown` a následně zavolat <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> metodu k získání objektu. Volající by měl pak přetypovávat návratovou hodnotu pro jakýkoli typ je vhodný. Pokud objekt je už nepotřebujete, volání <xref:System.Runtime.InteropServices.Marshal.Release%2A> pro uvolnění.  
  
 Tady je příklad volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> metoda a zpracování `IUnknown` objektu správně:  
  
```  
MyClass myclass;  
Object object;  
IntPtr pObj;  
Guid iid = Typeof(MyClass).Guid;  
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);     
if (NativeMethods.Succeeded(hr))   
{  
    try   
    {  
        object = Marshal.GetObjectForIUnknown(pObj);  
        myclass = object;  
    }  
    finally   
    {  
        Marshal.Release(pObj);  
    }  
}  
else   
{  
    // error calling QueryViewInterface  
}  
```  
  
> [!NOTE]
>  Následující metody se ví, předejte `IUnknown` objektu ukazatele jako typ <xref:System.IntPtr>. Jejich zpracování, jak je popsáno v této části.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### <a name="optional-out-parameters"></a>Volitelné [parametry out]  
 Vyhledejte parametry, které jsou definovány jako [out] datový typ (`int`, `object`, a tak dále) v modelu COM rozhraní, ale které jsou definovány jako pole stejného datového typu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototyp metody sestavení vzájemné spolupráce.  
  
 Některé COM rozhraní, jako například <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, nakládat [jako volitelné parametry out]. Pokud objekt není povinný, vrátí tato rozhraní COM `null` ukazatele jako hodnotu tohoto parametru místo vytvoření [out] objekt. Jedná se o účel. Pro tato rozhraní `null` ukazatele se předpokládá, že jako součást správné chování sady VSPackage, a není vrácena žádná chyba.  
  
 Protože CLR nepovoluje hodnotu parametr [out] bude `null`, část navrženého chování těchto rozhraní není přímo k dispozici v rámci spravovaného kódu. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Metody sestavení vzájemné spolupráce pro ovlivněné rozhraní tento problém obejít tak, že definujete relevantní parametry jako pole, protože modul CLR umožňuje předat `null` pole.  
  
 Spravované implementace tyto metody by měl umístit `null` pole do parametru, když není nutné nic vrátit. V opačném případě vytvořte pole s jedním prvkem správný typ a vložte návratová hodnota v poli.  
  
 Spravované metody, které se zobrazí informace z rozhraní s volitelné [out] Parametry získávají parametr jako pole. Právě zkontrolujte hodnoty první prvek pole. Pokud není `null`, první prvek zacházet, jako kdyby byly původní parametru.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Předávání konstanty v parametry ukazatele  
 Vyhledání parametrů, která jsou definována jako [v] ukazatele rozhraní modelu COM, ale které jsou definovány jako <xref:System.IntPtr> zadejte [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototyp metody sestavení vzájemné spolupráce.  
  
 K podobnému problému nastane, pokud rozhraní modelu COM předá zvláštní hodnota, například 0, -1 nebo hodnoty – 2, místo ukazatelem na objekt. Na rozdíl od [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], modul CLR neumožňuje konstanty pro přetypování jako objekty. Místo toho [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sestavení vzájemné spolupráce definuje jako parametr <xref:System.IntPtr> typu.  
  
 Spravované implementace z těchto metod zabere fakt, který <xref:System.IntPtr> třídy jsou obě `int` a `void *` konstruktory k vytvoření <xref:System.IntPtr> z objektu nebo celočíselné konstanty, podle potřeby.  
  
 Spravované metody, které přijímají <xref:System.IntPtr> byste použít parametry tohoto typu <xref:System.IntPtr> zadejte operátory převodu ke zpracování výsledků. Nejprve převeďte <xref:System.IntPtr> k `int` a testování proti relevantní celočíselné konstanty. Pokud žádné hodnoty shodují, převeďte jej na objekt požadovaného typu a pokračovat.  
  
 Příklady tohoto objektu, najdete v článku <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>OLE vrátit hodnoty předány jako [parametry out]  
 Hledat metody, které mají `retval` vrácená hodnota v rozhraní modelu COM, ale mají `int` vracet hodnotu a zobrazí se další [pole parametrem out] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototyp metody sestavení vzájemné spolupráce. By mělo být jasné, že tyto metody vyžadují speciální zacházení, protože [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sestavení vzájemné spolupráce metoda prototypy mít jeden parametr více než metody rozhraní modelu COM.  
  
 Mnoho rozhraní modelu COM, které se zabývají OLE aktivity odeslat informace o stavu OLE zpět na volající program uložené v `retval` návratovou hodnotu rozhraní. Namísto použití návratovou hodnotu odpovídající [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] metody sestavení vzájemné spolupráce poslat informace o zpět na volající program uložené v [out] pole parametrů.  
  
 Spravované implementace tyto metody by měly vytvořit pole s jedním prvkem stejného typu jako parametr [out] a vložit ho do parametru. Hodnota prvku pole musí být stejné jako odpovídající COM `retval`.  
  
 Spravované metody, které volají rozhraní tohoto typu by měl vyžádání prvního prvku mimo [out] pole. Tento element lze zacházet, jako by šlo `retval` návratová hodnota z odpovídající rozhraní modelu COM.  
  
## <a name="see-also"></a>Viz také  
 [Zařazování spolupráce](http://msdn.microsoft.com/en-us/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Zařazování spolupráce](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Řešení potíží s interoperabilitou](http://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [Spravovaná rozšíření VSPackages](../misc/managed-vspackages.md)