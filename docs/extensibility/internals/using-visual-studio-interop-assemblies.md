---
title: Pomocí sestavení Interop sady Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0db6e0e0d5014f09a84316143af40f410bc1b10
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722105"
---
# <a name="using-visual-studio-interop-assemblies"></a>Používání definičních sestavení sady Visual Studio
Sestavení vzájemné spolupráce sady Visual Studio umožňují spravovaným aplikacím přístup k rozhraním COM, která poskytují rozšiřitelnost sady Visual Studio. Existují některé rozdíly mezi přímými rozhraními COM a jejich definičními verzemi. Například HRESULTs se obvykle reprezentují jako celočíselné hodnoty a musí být zpracovány stejným způsobem jako výjimky a parametry (obzvláště výstupní parametry) jsou zpracovávány jinak.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Zpracování HRESULTs vrácených do spravovaného kódu z modelu COM
 Při volání rozhraní modelu COM ze spravovaného kódu, prověřte hodnotu HRESULT a v případě potřeby vyvolejte výjimku. Třída <xref:Microsoft.VisualStudio.ErrorHandler> obsahuje metodu <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, která vyvolá výjimku COM v závislosti na hodnotě HRESULT, která je předána.

 Ve výchozím nastavení <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> vyvolá výjimku pokaždé, když je předána hodnota HRESULT, která má hodnotu menší než nula. V případech, kdy tyto HRESULT jsou přijatelné hodnoty a žádná výjimka by měla být vyvolána, hodnoty dalších hodnot HRESULTs by měly být předány <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> po otestování hodnot. Pokud je hodnota HRESULT testována odpovídá všem hodnotám HRESULT, které jsou explicitně předány <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, není vyvolána žádná výjimka.

> [!NOTE]
> Třída <xref:Microsoft.VisualStudio.VSConstants> obsahuje konstanty pro běžné HRESULTs, například <xref:Microsoft.VisualStudio.VSConstants.S_OK> a <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTs, například <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> a <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> také poskytuje metody <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> a <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, které odpovídají ÚSPĚŠNÝm a NEZDAŘENým makrům v modelu COM.

 Zvažte například následující volání funkce, ve kterém <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> přípustný návratová hodnota, ale jakákoli jiná hodnota HRESULT menší než nula představuje chybu.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Pokud je k dispozici více než jedna přijatelná návratová hodnota, lze do seznamu volání <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> pouze připojit další hodnoty HRESULT.

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Vrácení HRESULTs do modelu COM ze spravovaného kódu
 Pokud nedojde k žádné výjimce, spravovaný kód vrátí <xref:Microsoft.VisualStudio.VSConstants.S_OK> funkce COM, která ji volala. Zprostředkovatel komunikace s objekty COM podporuje běžné výjimky, které jsou silně typované ve spravovaném kódu. Například metoda, která přijímá nepřijatelný `null` argument vyvolá <xref:System.ArgumentNullException>.

 Pokud si nejste jistí, jakou výjimku chcete vyvolat, ale víte, že HRESULT, kterou chcete vrátit do modelu COM, lze použít metodu <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> k vyvolání příslušné výjimky. To funguje i s nestandardní chybou, například <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> se pokusí mapovat HRESULT předané na výjimku silného typu. Pokud to nemůže, vyvolá místo toho obecnou výjimku modelu COM. Konečný výsledek je, že hodnota HRESULT, kterou předáte <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> ze spravovaného kódu, se vrátí do funkce COM, která ji zavolala.

> [!NOTE]
> Výjimky budou mít vliv na ohrožení zabezpečení a jsou určeny k označení abnormálních podmínek programu. Podmínky, ke kterým dochází často, by měly být zpracovány jako vložené místo vyvolané výjimky.

## <a name="iunknown-parameters-passed-as-type-void"></a>Parametry IUnknown byly předány jako typ void * *.
 Vyhledejte parametry [out], které jsou definovány jako typ `void **` v rozhraní modelu COM, které jsou definovány jako `[``iid_is``]` v prototypu metody sestavení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop.

 V některých případech rozhraní COM generuje objekt `IUnknown` a rozhraní COM ho potom předává jako typ `void **`. Tato rozhraní jsou obzvláště důležitá, protože pokud je proměnná definována jako [out] v IDL, pak objekt `IUnknown` je počítán odkazem s metodou `AddRef`. Nevracení paměti dojde v případě, že se objekt nezpracovává správně.

> [!NOTE]
> Objekt `IUnknown` vytvořený rozhraním COM a vrácený proměnnou [out] způsobuje nevrácení paměti, pokud není explicitně uvolněn.

 Spravované metody, které zpracovávají takové objekty, by měly považovat <xref:System.IntPtr> jako ukazatel na objekt `IUnknown` a volat metodu <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> pro získání objektu. Volající by pak měl přetypovat návratovou hodnotu na libovolný typ. Pokud už objekt není potřeba, zavolejte <xref:System.Runtime.InteropServices.Marshal.Release%2A> a vyžádejte si ho.

 Následuje příklad volání metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> a správné zpracování objektu `IUnknown`:

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
> Následující metody jsou známy, aby předávaly `IUnknown` ukazatelé objektu jako typ <xref:System.IntPtr>. Zpracujte je podle pokynů v této části.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Volitelné parametry [out]
 Vyhledá parametry, které jsou definovány jako datový typ [out] (`int`, `object` atd.) v rozhraní COM, ale které jsou definovány jako pole stejného datového typu v prototypu metody spolupráce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 Některá rozhraní COM, například <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, považují parametry [out] za volitelné. Pokud objekt není vyžadován, tato rozhraní COM vrátí `null` ukazatel jako hodnotu tohoto parametru namísto vytvoření objektu [out]. To je záměrné. Pro tato rozhraní se `null` ukazatelů předpokládají jako součást správného chování VSPackage a není vrácena žádná chyba.

 Vzhledem k tomu, že modul CLR nepovoluje, aby byla hodnota parametru [out] `null`, část navrženého chování těchto rozhraní není přímo k dispozici ve spravovaném kódu. Metody sestavení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vzájemné spolupráce pro ovlivněná rozhraní fungují na problém definováním relevantních parametrů jako pole, protože modul CLR umožňuje předat `null` pole.

 Spravované implementace těchto metod by měly do parametru umístit `null` pole, pokud není nic vráceno. V opačném případě vytvořte pole s jedním prvkem správného typu a vložte vrácenou hodnotu do pole.

 Spravované metody, které přijímají informace z rozhraní s nepovinnými parametry [out] obdrží parametr jako pole. Pouze prověřte hodnotu prvního prvku pole. Pokud není `null`, považovat první prvek, jako by to byl původní parametr.

## <a name="passing-constants-in-pointer-parameters"></a>Předávání konstant v parametrech ukazatele
 Vyhledejte parametry, které jsou definovány jako [in] ukazatelů v rozhraní COM, ale které jsou definovány jako typ <xref:System.IntPtr> v prototypu metody sestavení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop.

 K podobnému problému dochází, když rozhraní COM předá speciální hodnotu, například 0,-1 nebo-2, místo ukazatele na objekt. Na rozdíl od [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] modul CLR nepovoluje přetypování konstant jako objektů. Místo toho definiční sestavení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] definuje parametr jako typ <xref:System.IntPtr>.

 Spravované implementace těchto metod by měly využít fakt, že třída <xref:System.IntPtr> obsahuje konstruktory `int` a `void *` k vytvoření <xref:System.IntPtr> z objektu nebo celočíselné konstanty (podle potřeby).

 Spravované metody, které přijímají parametry <xref:System.IntPtr> tohoto typu, by měly použít operátory převodu typu <xref:System.IntPtr> pro zpracování výsledků. Nejprve převeďte <xref:System.IntPtr> na `int` a otestujte je proti relevantním celočíselným konstantám. Pokud se žádné hodnoty neshodují, převeďte je na objekt požadovaného typu a pokračujte.

 Příklady najdete v tématu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.

## <a name="ole-return-values-passed-as-out-parameters"></a>Návratové hodnoty OLE předané jako parametry [out]
 Vyhledejte metody, které mají `retval` návratovou hodnotu v rozhraní COM, ale které mají `int` návratovou hodnotu a další parametr [out] v prototypu metody sestavení [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Interop. Mělo by být jasné, že tyto metody vyžadují speciální zpracování, protože prototypy metody sestavení Interop [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mají jeden další parametr než metody rozhraní modelu COM.

 Mnoho rozhraní COM, která se týkají aktivity OLE, odesílají informace o stavu OLE zpět volajícímu programu uloženému v `retval` návratové hodnotě rozhraní. Namísto použití návratové hodnoty odpovídající metody sestavení Interop [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] odesílají informace zpět do volajícího programu uloženého v parametru pole [out].

 Spravované implementace těchto metod by měly vytvořit pole s jedním prvkem stejného typu jako parametr [out] a umístit ho do parametru. Hodnota prvku pole by měla být stejná jako odpovídající `retval` COM.

 Spravované metody, které volají rozhraní tohoto typu, by měly načíst první prvek z pole [out]. Tento element může být zpracován, jako by se jednalo o `retval` návratovou hodnotu z odpovídajícího rozhraní COM.

## <a name="see-also"></a>Viz také:
- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)