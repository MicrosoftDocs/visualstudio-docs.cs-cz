---
title: Použití sestavení interop sady Visual Studio | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5926b2cce217565c889c7ef2eeef877691101ed6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704134"
---
# <a name="using-visual-studio-interop-assemblies"></a>Používání definičních sestavení sady Visual Studio
Meziop sestavení sady Visual Studio umožňují spravovaným aplikacím přístup k rozhraním COM, které poskytují rozšiřitelnost sady Visual Studio. Existují určité rozdíly mezi přímými rozhraními COM a jejich interop verzemi. Například HRESULTs jsou obecně reprezentovány jako int hodnoty a je třeba zacházet stejným způsobem jako výjimky a parametry (zejména mimo parametry) jsou zpracovány odlišně.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Zpracování HRESULTs vrácené do spravovaného kódu z COM
 Při volání rozhraní COM ze spravovaného kódu zkontrolujte hodnotu HRESULT a v případě potřeby vyvolejte výjimku. Třída <xref:Microsoft.VisualStudio.ErrorHandler> obsahuje <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> metodu, která vyvolá výjimku COM, v závislosti na hodnotě HRESULT předány.

 Ve výchozím <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> nastavení vyvolá výjimku vždy, když je předán HRESULT, který má hodnotu menší než nula. V případech, kdy jsou tyto HRESULTs přijatelné hodnoty a žádná výjimka by měla <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> být vyvolána, hodnoty dalšíhvýsledky by měly být předány po testování hodnoty. Pokud HRESULT testovánodpovídá všechny hodnoty HRESULT <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>explicitně předány , není vyvolána žádná výjimka.

> [!NOTE]
> Třída <xref:Microsoft.VisualStudio.VSConstants> obsahuje <xref:Microsoft.VisualStudio.VSConstants.S_OK> konstanty pro běžné HRESULTS, <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>například a , <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> a <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTS, například a . <xref:Microsoft.VisualStudio.VSConstants>poskytuje také <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> metody a, které odpovídají makra SUCCEEDED a FAILED v com.

 Zvažte například následující volání funkce, ve kterém <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> je přijatelná vrácená hodnota, ale jakékoli jiné HRESULT menší než nula představuje chybu.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Pokud existuje více než jednu přijatelnou vrácenou hodnotu, další hodnoty HRESULT <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>lze připojit pouze do seznamu ve volání .

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Vrácení výsledků HRESULTS com ze spravovaného kódu
 Pokud nedojde k žádné výjimce, spravovaný kód se vrátí <xref:Microsoft.VisualStudio.VSConstants.S_OK> do funkce COM, která jej volala. Com interop podporuje běžné výjimky, které jsou silně zadali ve spravovaném kódu. Například metoda, která obdrží nepřijatelný `null` argument, <xref:System.ArgumentNullException>vyvolá .

 Pokud si nejste jisti, kterou výjimku vyvolat, ale víte, HRESULT, <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> které chcete vrátit do COM, můžete použít metodu k vyvolání příslušné výjimky. To funguje i s nestandardní chybou, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>například . <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>pokusí se namapovat HRESULT předána na výjimku silného typu. Pokud nemůže, vyvolá obecnou výjimku COM místo. Konečným výsledkem je, že HRESULT předáte <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> ze spravovaného kódu je vrácena do funkce COM, která ji volala.

> [!NOTE]
> Výjimky ohrožují výkon a jsou určeny k označení neobvyklých podmínek programu. Podmínky, které se vyskytují často by měly být zpracovány vřádí, namísto vyvolána výjimka.

## <a name="iunknown-parameters-passed-as-type-void"></a>Parametry IUnknown předané jako Type void**
 Vyhledejte parametry [out], které `void **` jsou definovány jako typ v `[``iid_is``]` rozhraní [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] COM, ale které jsou definovány jako v prototypu metody meziop sestavení.

 V některých případě rozhraní `IUnknown` COM generuje objekt a rozhraní `void **`COM jej pak předá jako typ . Tato rozhraní jsou obzvláště důležité, protože pokud je proměnná definována `IUnknown` jako [out] v `AddRef` IDL, pak je objekt spočítán s metodou. Nevracení paměti dochází, pokud objekt není správně zpracována.

> [!NOTE]
> Objekt `IUnknown` vytvořený rozhraním COM a vrácený v proměnné [out] způsobí nevracení paměti, pokud není explicitně uvolněno.

 Spravované metody, které zpracovávají tyto objekty by měl y považovat <xref:System.IntPtr> za ukazatel na objekt `IUnknown` a volání <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> metody k získání objektu. Volající by pak přetypovat vrácenou hodnotu bez ohledu na typ je vhodné. Pokud objekt již není potřeba, volání <xref:System.Runtime.InteropServices.Marshal.Release%2A> jej uvolnit.

 Následuje příklad volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> metody a správné `IUnknown` zpracování objektu:

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
> Následující metody jsou známy předat `IUnknown` ukazatele <xref:System.IntPtr>objektu jako typ . Zacházejte s nimi, jak je popsáno v této části.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Volitelné parametry [out]
 Vyhledejte parametry, které jsou definovány jako`int` `object`datový typ [out] ( , , a tak dále) v rozhraní [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] MODELU COM, ale které jsou definovány jako pole stejného datového typu v prototypu metody sestavení interop.

 Některá rozhraní COM, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>například , považují parametry [out] za volitelné. Pokud objekt není vyžadován, tato rozhraní `null` COM vrátí ukazatel jako hodnotu tohoto parametru namísto vytvoření objektu [out]. Toto chování je úmyslné. Pro tato rozhraní `null` ukazatele jsou považovány za součást správné chování VSPackage a je vrácena žádná chyba.

 Vzhledem k tomu, že CLR neumožňuje hodnotu parametru [out] `null`být , část navržené chování těchto rozhraní není přímo k dispozici v rámci spravovaného kódu. Interop [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metody sestavení pro ovlivněné rozhraní obejít problém definováním příslušné parametry jako pole, protože CLR umožňuje předávání `null` polí.

 Spravované implementace těchto metod by `null` měl y dát pole do parametru, pokud není nic, co má být vráceno. V opačném případě vytvořte jednoelementové pole správného typu a vložte vrácenou hodnotu do pole.

 Spravované metody, které přijímají informace z rozhraní s volitelnými parametry [out], přijímají parametr jako pole. Stačí zkontrolovat hodnotu první prvek pole. Pokud tomu `null`tak není , zacházejte s prvním prvkem, jako by se jednalo o původní parametr.

## <a name="passing-constants-in-pointer-parameters"></a>Předávání konstant v parametrech ukazatele
 Vyhledejte parametry, které jsou definovány jako ukazatele [in] v <xref:System.IntPtr> rozhraní COM, ale které jsou definovány jako typ v prototypu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metody sestavení interop.

 K podobnému problému dochází, když rozhraní COM předá zvláštní hodnotu, například 0, -1 nebo -2, namísto ukazatele objektu. Na [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]rozdíl od CLR neumožňuje konstanty, které mají být přetypována jako objekty. Místo toho [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interop sestavení definuje parametr <xref:System.IntPtr> jako typ.

 Spravované implementace těchto metod by měly využít <xref:System.IntPtr> skutečnosti, `int` `void *` že třída má <xref:System.IntPtr> jak konstruktory a vytvořit z objektu nebo celé číslo konstanty, podle potřeby.

 Spravované metody, <xref:System.IntPtr> které přijímají parametry <xref:System.IntPtr> tohoto typu, by měly ke zpracování výsledků používat operátory převodu typu. Nejprve <xref:System.IntPtr> převeďte na `int` a otestujte jej proti příslušným řadivčím konstantám celého čísla. Pokud se žádné hodnoty neshodují, převeďte je na objekt požadovaného typu a pokračujte.

 Příklady tohoto viz <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.

## <a name="ole-return-values-passed-as-out-parameters"></a>Vrácené hodnoty OLE předané jako parametry [out]
 Vyhledejte metody, `retval` které mají vrácenou hodnotu v `int` rozhraní COM, ale které mají [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vrácenou hodnotu a další parametr pole [out] v prototypu metody sestavení interop. Mělo by být jasné, že tyto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metody vyžadují zvláštní zpracování, protože prototypy metody sestavení interop mají jeden další parametr než metody rozhraní COM.

 Mnoho rozhraní COM, které se zabývají aktivitou OLE, odesílá `retval` informace o stavu OLE zpět volajícímu programu uloženému v návratové hodnotě rozhraní. Namísto použití vrácené hodnoty [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] odeslat odpovídající metody sestavení interop informace zpět do volajícího programu uloženého v parametru [out] pole.

 Spravované implementace těchto metod by měly vytvořit jednoelementové pole stejného typu jako parametr [out] a vložit jej do parametru. Hodnota prvku pole by měla být stejná `retval`jako příslušná hodnota COM .

 Spravované metody, které volají rozhraní tohoto typu by měl yvytáhnout první prvek z pole [out]. Tento prvek lze považovat, jako `retval` by se jednalo o vrácenou hodnotu z odpovídajícího rozhraní COM.

## <a name="see-also"></a>Viz také
- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)
