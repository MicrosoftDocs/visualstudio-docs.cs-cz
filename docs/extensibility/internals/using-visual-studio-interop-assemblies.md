---
title: Pomocí sady Visual Studio spolupráce – sestavení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca0ff9a75d72bc723b767a43f12123094a520644
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31146816"
---
# <a name="using-visual-studio-interop-assemblies"></a>Pomocí sady Visual Studio spolupráce – sestavení
Visual Studio sestavení vzájemné spolupráce povolit spravované aplikace pro přístup k rozhraní modelu COM, která zajistí možnosti rozšíření sady Visual Studio. Existují určité rozdíly mezi přímých rozhraní COM a jejich vzájemné spolupráce verze. Hodnoty HRESULT jsou obecně vyjádřené hodnoty int a je nutné zacházet stejným způsobem jako výjimky a parametry (zejména výstupní parametry) jsou zpracovávat odděleně.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Hodnoty HRESULT zpracování vrácen do spravovaného kódu z modelu COM  
 Při volání rozhraní modelu COM ze spravovaného kódu, zkontrolujte hodnotu HRESULT a způsobí výjimku, pokud je to nutné. <xref:Microsoft.VisualStudio.ErrorHandler> Třída obsahuje <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> metoda, která vyvolává k výjimce modelu COM., v závislosti na hodnotě hodnota HRESULT do ní předán.  
  
 Ve výchozím nastavení <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> vyvolá výjimku, vždy, když je předán HRESULT, který má hodnotu menší než nula. V případě přípustné hodnoty jsou tyto hodnoty HRESULT a by měl být vyvolána žádná výjimka, by měla být předána hodnoty další hodnoty HRESULT <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> po otestování hodnoty. Pokud HRESULT testuje odpovídá žádné hodnoty HRESULT explicitně předaný <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, nedojde k výjimce.  
  
> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants> Třída obsahuje konstanty pro běžné hodnoty HRESULT, například <xref:Microsoft.VisualStudio.VSConstants.S_OK> a <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hodnoty HRESULT, například <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> a <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> také poskytuje <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> a <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> metody, které odpovídají úspěšné a NEÚSPĚŠNÉ makra v modelu COM.  
  
 Zvažte například následující volání funkce, ve kterém <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> je přijatelné návratovou hodnotu, ale jiné HRESULT menší než nula. představuje chybu.  
  
 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 Pokud máte více než jeden přijatelné návratové hodnoty, může být další hodnoty HRESULT právě přidán do seznamu ve volání <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.  
  
 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Hodnoty HRESULT vrácením COM ze spravovaného kódu  
 Pokud dojde k žádná výjimka, spravovaný kód vrátí <xref:Microsoft.VisualStudio.VSConstants.S_OK> funkce COM, která je volána. Zprostředkovatel komunikace s objekty COM podporuje společné výjimky, které jsou silného typu ve spravovaném kódu. Například metoda, která přijímá nepřijatelné `null` argument vyvolává <xref:System.ArgumentNullException>.  
  
 Pokud si nejste jistí které výjimkou výjimku, ale znáte hodnota HRESULT chcete vrátit do modelu COM, můžete použít <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> metodu pro příslušné výjimku. Tento postup funguje i s nestandardní chybu, například <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> pokusy o mapování hodnota HRESULT předán do ní silného typu výjimka. Pokud ne, vyvolá k obecné výjimce modelu COM. místo. Konečným výsledkem je, že hodnota HRESULT předáte <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> ze spravovaného kódu, které se vrátí do funkce COM, která je volána.  
  
> [!NOTE]
>  Snížit výkon, výjimky, které slouží k označení neobvyklého podmínky. Podmínky, které dochází často, by měly být zpracovávaný vložené, místo vyvolaná výjimka.  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>Parametry IUnknown předány jako typ void**  
 Vyhledejte [parametry, které jsou definovány jako typ out] `void **` v modelu COM rozhraní, ale které jsou definovány jako `[``iid_is``]` v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sestavení vzájemné spolupráce metoda prototypu.  
  
 V některých případech vygeneruje rozhraní modelu COM `IUnknown` objekt a rozhraní COM pak předá ji jako typ `void **`. Tato rozhraní jsou zvlášť důležité, protože pokud proměnnou je definován jako [out] v IDL, pak se `IUnknown` objekt je odkaz počítá s `AddRef` metoda. Nevrácená paměť systému nastane, pokud objekt není správně zpracovat.  
  
> [!NOTE]
>  `IUnknown` Objektu vytvořené rozhraní COM a vrátí proměnnou [out] dojde nevrácená paměť systému, pokud se explicitně neuvolní.  
  
 Spravované metody, které zpracovávají tyto objekty by měly zpracovávat <xref:System.IntPtr> jako ukazatel na `IUnknown` objektu a volání <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> metodu k získání objektu. Volající by pak přetypování návratovou hodnotu pro libovolnou typ je vhodný. Pokud objekt je již nepotřebujete, volání <xref:System.Runtime.InteropServices.Marshal.Release%2A> pro uvolnění.  
  
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
>  Tyto metody jsou známé předat `IUnknown` ukazatele na objekt jako typ <xref:System.IntPtr>. Zpracování je, jak je popsáno v této části.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>Volitelné [parametry out]  
 Vyhledejte parametry, které jsou definovány jako [out] datový typ (`int`, `object`a tak dále) v modelu COM rozhraní, ale které jsou definovány jako pole stejného typu dat ve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sestavení vzájemné spolupráce metoda prototypu.  
  
 Některé COM rozhraní, jako například <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, s nakládat [jako volitelné parametry out]. Pokud objekt není povinný, vrátí tato rozhraní COM `null` ukazatel jako hodnotu tohoto parametru místo vytvoření objektu [out]. Toto je záměrné. Pro tyto rozhraní `null` ukazatele se předpokládá, že jako součást správné chování VSPackage a vrácena žádná chyba.  
  
 Protože modulu CLR není povolena hodnota parametru [out] jako `null`, součástí navrženou chování těchto rozhraní není přímo k dispozici v rámci spravovaného kódu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Metody sestavení vzájemné spolupráce pro ovlivněné rozhraní tento problém obejít tak, že definujete relevantní parametry jako pole, protože modul CLR umožňuje předat `null` pole.  
  
 Spravované implementace tyto metody by měla put `null` pole do parametru, když není co má být vrácen. Jinak vytvořit jeden element pole správného typu a put návratovou hodnotu v poli.  
  
 Spravované metody, které přijímají informace z rozhraní s volitelné [out] Parametry získávají parametr jako pole. Jenom zkontrolujte hodnotu první prvek pole. Pokud není `null`, považovat první prvek, jako by šlo parametr původní.  
  
## <a name="passing-constants-in-pointer-parameters"></a>Předávání konstanty v parametrech ukazatele  
 Vyhledejte parametry, které jsou definovány jako [v] ukazatele v rozhraní modelu COM, ale které jsou definovány jako <xref:System.IntPtr> zadejte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sestavení vzájemné spolupráce metoda prototypu.  
  
 Podobné problém nastane, když rozhraní modelu COM předá speciální hodnotu, jako jsou 0, -1 nebo -2, místo ukazatele na objekt. Na rozdíl od [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], modul CLR neumožňuje konstanty být přetypovat jako objekty. Místo toho [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sestavení vzájemné spolupráce definuje jako parametr <xref:System.IntPtr> typu.  
  
 Spravované implementace z těchto metod by měl využít výhod fakt, na který <xref:System.IntPtr> třída má oba `int` a `void *` konstruktory k vytvoření <xref:System.IntPtr> z objektu nebo celočíselná konstanta jako vhodné.  
  
 Spravované metody, které přijímají <xref:System.IntPtr> parametry tento typ měli používat <xref:System.IntPtr> zadejte operátory převodu pro zpracování výsledků. Nejprve převeďte <xref:System.IntPtr> k `int` a testování proti relevantní celočíselné konstanty. Pokud žádné hodnoty shodují, převést na objekt požadovaný typ a pokračovat.  
  
 Příklady tohoto najdete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE vrátit hodnoty předány jako [parametry out]  
 Vyhledejte metody, které mají `retval` návratová hodnota v rozhraní modelu COM, ale mají `int` vracet hodnotu a další [out] parametr pole v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sestavení vzájemné spolupráce metoda prototypu. By mělo být jasné, že tyto metody vyžadují zvláštní zpracování, protože [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sestavení vzájemné spolupráce metoda prototypy mít jeden parametr více než metody rozhraní COM.  
  
 Mnoho rozhraní modelu COM, které pracují s OLE aktivity odeslat informace o stavu OLE zpět volací program uložené v `retval` vrátit hodnotu rozhraní. Místo použití návratovou hodnotu, odpovídající [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sestavení vzájemné spolupráce metody odeslat informace zpět do volání programu uložených v [out] parametr pole.  
  
 Spravované implementace z těchto metod by měl vytvořit jeden element pole stejného typu jako parametr [out] a umístí jej v parametru. Hodnota elementu pole by měl být stejný jako příslušný COM `retval`.  
  
 Spravované metody, které volají rozhraní tento typ měli pull první prvek mimo [out] pole. Tento element lze zacházet, jako by šlo `retval` vrátit hodnotu z odpovídající rozhraní modelu COM.  
  
## <a name="see-also"></a>Viz také  
 [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)