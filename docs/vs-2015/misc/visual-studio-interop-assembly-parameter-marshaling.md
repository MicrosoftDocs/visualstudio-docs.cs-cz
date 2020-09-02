---
title: Zařazování parametrů sestavení Interop sady Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: ac95c40b356c542da323a3ea3744827087f2d840
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686928"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Zařazování parametrů sestavení Interop sady Visual Studio
Rozhraní VSPackage, která jsou napsána ve spravovaném kódu, mohou být pravděpodobně volána nebo volána nespravovaným kódem COM. Obvykle jsou argumenty metody transformovány nebo zařazeny automaticky zařazováním Interop. Někdy se ale argumenty nedají transformovat jednoduchým způsobem. V těchto případech se parametry prototypu metody sestavení používají k co nejpřesněji shodě parametrů funkce modelu COM. Další informace najdete v tématu [zařazování Interop](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Obecné návrhy  
  
##### <a name="read-the-reference-documentation"></a>Přečtěte si referenční dokumentaci  
 Účinný způsob, jak zjistit problémy s interoperabilitou, je přečíst si referenční dokumentaci pro každou metodu.  
  
 Referenční dokumentace pro každou metodu obsahuje tři relevantní oddíly:  
  
- [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]Prototyp funkce modelu COM.  
  
- Prototyp metody sestavení Interop.  
  
- Seznam parametrů modelu COM a stručný popis každého z nich.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>Vyhledání rozdílů mezi těmito dvěma prototypy  
 Většina problémů s interoperabilitou je odvozena z neshody mezi definicí konkrétního typu v rozhraní COM a definicí stejného typu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sestaveních spolupráce. Zvažte například rozdíl v možnosti předání `null` hodnoty v parametru [out]. Je nutné vyhledat rozdíly mezi těmito dvěma prototypy a vzít v úvahu jejich důsledky pro předávané údaje.  
  
##### <a name="read-the-parameter-definitions"></a>Přečtěte si definice parametrů  
 Přečtěte si definice parametrů. Model COM je méně striktní než modul CLR (Common Language Runtime), který slouží k kombinování různých typů dat v jednom parametru. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Rozhraní COM plně využívají tuto flexibilitu. Libovolný parametr, který může předat nebo vyžadovat nestandardní hodnotu nebo typ dat, jako je například konstantní hodnota v parametru ukazatele, by měl být popsán jako v dokumentaci.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>Objekty IUnknown předané jako typ void * *  
 Vyhledejte parametry [out], které jsou definovány jako typ `void **` v rozhraní COM, ale jsou definovány jako `[``iid_is``]` v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototypu metody sestavení Interop.  
  
 V některých případech rozhraní COM generuje `IUnknown` objekt a rozhraní com ho potom předává jako typ `void **` . Tato rozhraní jsou obzvláště důležitá, protože pokud je proměnná definována jako [out] v IDL, pak `IUnknown` je objekt počítán odkazem pomocí `AddRef` metody. Nevracení paměti dojde v případě, že se objekt nezpracovává správně.  
  
> [!NOTE]
> `IUnknown`Objekt vytvořený rozhraním com a vrácený v proměnné [out] způsobuje nevrácení paměti, pokud není explicitně uvolněn.  
  
 Spravované metody, které zpracovávají takové objekty by měly být považovány <xref:System.IntPtr> za ukazatel na `IUnknown` objekt a volat <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> metodu pro získání objektu. Volající by pak měl přetypovat návratovou hodnotu na libovolný typ. Pokud objekt již není potřeba, zavolejte <xref:System.Runtime.InteropServices.Marshal.Release%2A> k jeho vydání.  
  
 Následuje příklad volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> metody a správné manipulace s `IUnknown` objektem:  
  
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
> Následující metody jsou známy pro předání `IUnknown` ukazatelů na objekty jako typ <xref:System.IntPtr> . Zpracujte je podle pokynů v této části.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### <a name="optional-out-parameters"></a>Volitelné parametry [out]  
 Vyhledejte parametry, které jsou definovány jako datový typ [out] ( `int` , `object` a tak dále) v rozhraní COM, ale které jsou definovány jako pole stejného datového typu v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototypu metody sestavení Interop.  
  
 Některá rozhraní COM, jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> je například, považovat parametry [out] za volitelné. Pokud objekt není vyžadován, tato rozhraní COM vrátí `null` ukazatel jako hodnotu tohoto parametru namísto vytvoření objektu [out]. Toto chování je úmyslné. Pro tato rozhraní `null` jsou ukazatele považovány za součást správného chování VSPackage a není vrácena žádná chyba.  
  
 Vzhledem k tomu, že modul CLR nepovoluje, aby byla hodnota parametru [out] `null` , součástí navrženého chování těchto rozhraní není přímo k dispozici ve spravovaném kódu. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Metody sestavení vzájemné spolupráce pro ovlivněná rozhraní řeší problém definováním relevantních parametrů jako pole, protože modul CLR umožňuje předávání `null` polí.  
  
 Spravované implementace těchto metod by měly vložit `null` pole do parametru, pokud není nic vráceno. V opačném případě vytvořte pole s jedním prvkem správného typu a vložte vrácenou hodnotu do pole.  
  
 Spravované metody, které přijímají informace z rozhraní s nepovinnými parametry [out] obdrží parametr jako pole. Pouze prověřte hodnotu prvního prvku pole. Pokud není `null` , považovat první prvek, jako by to byl původní parametr.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Předávání konstant v parametrech ukazatele  
 Vyhledejte parametry, které jsou definovány jako [in] ukazatelů v rozhraní modelu COM, které jsou definovány jako <xref:System.IntPtr> typ v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototypu metody sestavení Interop.  
  
 K podobnému problému dochází, když rozhraní COM předá speciální hodnotu, například 0,-1 nebo – 2, místo ukazatele na objekt. Na rozdíl od [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , modul CLR nepovoluje, aby byly konstanty přetypování jako objekty. Místo toho [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] definiční sestavení definuje parametr jako <xref:System.IntPtr> typ.  
  
 Spravované implementace těchto metod by měly využít skutečnost, že <xref:System.IntPtr> Třída má obojí `int` a `void *` konstruktory pro vytvoření <xref:System.IntPtr> z objektu nebo celočíselné konstanty (podle potřeby).  
  
 Spravované metody, které přijímají <xref:System.IntPtr> parametry tohoto typu, by měly použít <xref:System.IntPtr> operátory převodu typu pro zpracování výsledků. Nejprve převeďte <xref:System.IntPtr> na `int` a otestujte pomocí relevantních celočíselných konstant. Pokud se žádné hodnoty neshodují, převeďte je na objekt požadovaného typu a pokračujte.  
  
 Příklady naleznete v tématech <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>Návratové hodnoty OLE předané jako parametry [out]  
 Vyhledejte metody, které mají `retval` vrácenou hodnotu v rozhraní modelu COM, ale mají `int` vrácenou hodnotu a další parametr [out] v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototypu metody sestavení Interop. Mělo by být jasné, že tyto metody vyžadují speciální zpracování, protože [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototypy metody sestavení Interop mají jeden další parametr než metody rozhraní modelu COM.  
  
 Mnoho rozhraní COM, která se týkají aktivity OLE, odesílají informace o stavu OLE zpět volajícímu programu uloženému v `retval` návratové hodnotě rozhraní. Namísto použití návratové hodnoty, odpovídající [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] metody sestavení vzájemné spolupráce odesílají informace zpět volajícímu programu uloženému v parametru pole [out].  
  
 Spravované implementace těchto metod by měly vytvořit pole s jedním prvkem stejného typu jako parametr [out] a umístit ho do parametru. Hodnota prvku pole by měla být stejná jako odpovídající model COM `retval` .  
  
 Spravované metody, které volají rozhraní tohoto typu, by měly načíst první prvek z pole [out]. Tento element lze zacházet, jako by šlo o `retval` návratovou hodnotu z odpovídajícího rozhraní modelu COM.  
  
## <a name="see-also"></a>Viz také  
 [Zařazování spolupráce](https://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Zařazování spolupráce](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Řešení potíží s interoperabilitou](https://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [Spravované VSPackage](../misc/managed-vspackages.md)