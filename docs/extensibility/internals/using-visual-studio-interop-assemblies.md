---
title: Pomocí sestavení Interop sady Visual Studio | Microsoft Docs
description: Přečtěte si, jak sestavení Interop sady Visual Studio umožňuje spravovaným aplikacím přístup k rozhraním COM, která poskytují rozšiřitelnost sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1253f5e7197f587e4a5e62365b42cb5040010666
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090665"
---
# <a name="using-visual-studio-interop-assemblies"></a>Používání definičních sestavení sady Visual Studio
Sestavení vzájemné spolupráce sady Visual Studio umožňují spravovaným aplikacím přístup k rozhraním COM, která poskytují rozšiřitelnost sady Visual Studio. Existují některé rozdíly mezi přímými rozhraními COM a jejich definičními verzemi. Například HRESULTs se obvykle reprezentují jako celočíselné hodnoty a musí být zpracovány stejným způsobem jako výjimky a parametry (obzvláště výstupní parametry) jsou zpracovávány jinak.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Zpracování HRESULTs vrácených do spravovaného kódu z modelu COM
 Při volání rozhraní modelu COM ze spravovaného kódu, prověřte hodnotu HRESULT a v případě potřeby vyvolejte výjimku. <xref:Microsoft.VisualStudio.ErrorHandler>Třída obsahuje <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> metodu, která VYVOLÁ výjimku com v závislosti na hodnotě HRESULT, která je předána do ní.

 Ve výchozím nastavení <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> vyvolá výjimku, kdykoli je předána hodnota HRESULT, která má hodnotu menší než nula. V případech, kdy tyto HRESULTs jsou přijatelné hodnoty a žádná výjimka by měla být vyvolána, hodnoty dalších HRESULTs by měly být předány <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> Po otestování hodnot. Pokud testovaný HRESULT odpovídá všem hodnotám HRESULT, které jsou explicitně předány do <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> , není vyvolána žádná výjimka.

> [!NOTE]
> <xref:Microsoft.VisualStudio.VSConstants>Třída obsahuje konstanty pro běžné HRESULTS, například a a <xref:Microsoft.VisualStudio.VSConstants.S_OK> <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTS, například <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> a <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> . <xref:Microsoft.VisualStudio.VSConstants> poskytuje také <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> metody a <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> , které odpovídají úspěšným a neúspěšným makrům v modelu COM.

 Zvažte například následující volání funkce, ve kterém <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> je přijatelné návratové hodnoty, ale jakákoli jiná hodnota HRESULT menší než nula představuje chybu.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Pokud je k dispozici více než jedna přijatelná návratová hodnota, lze do seznamu v volání metody přidat pouze další hodnoty HRESULT <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> .

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Vrácení HRESULTs do modelu COM ze spravovaného kódu
 Pokud nedojde k žádné výjimce, spravovaný kód vrátí <xref:Microsoft.VisualStudio.VSConstants.S_OK> funkci com, která ji volala. Zprostředkovatel komunikace s objekty COM podporuje běžné výjimky, které jsou silně typované ve spravovaném kódu. Například metoda, která přijímá nepřijatelný `null` argument <xref:System.ArgumentNullException> , vyvolá.

 Pokud si nejste jistí, která výjimka má být vyvolána, ale víte, že HRESULT, kterou chcete vrátit do modelu COM, lze použít <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> metodu k vyvolání příslušné výjimky. To funguje i s nestandardní chybou, například <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> . <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> pokusí se namapovat HRESULT předané na výjimku silného typu. Pokud to nemůže, vyvolá místo toho obecnou výjimku modelu COM. Konečný výsledek je, že hodnota HRESULT, kterou předáte <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> ze spravovaného kódu, se vrátí do funkce com, která ji zavolala.

> [!NOTE]
> Výjimky budou mít vliv na ohrožení zabezpečení a jsou určeny k označení abnormálních podmínek programu. Podmínky, ke kterým dochází často, by měly být zpracovány jako vložené místo vyvolané výjimky.

## <a name="iunknown-parameters-passed-as-type-void"></a>Parametry IUnknown byly předány jako typ void * *.
 Vyhledejte parametry [out], které jsou definovány jako typ `void **` v rozhraní COM, ale jsou definovány jako `[``iid_is``]` v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypu metody sestavení Interop.

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

## <a name="optional-out-parameters"></a>Volitelné parametry [out]
 Vyhledejte parametry, které jsou definovány jako datový typ [out] ( `int` , `object` a tak dále) v rozhraní COM, ale které jsou definovány jako pole stejného datového typu v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypu metody sestavení Interop.

 Některá rozhraní COM, jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> je například, považovat parametry [out] za volitelné. Pokud objekt není vyžadován, tato rozhraní COM vrátí `null` ukazatel jako hodnotu tohoto parametru namísto vytvoření objektu [out]. Toto chování je úmyslné. Pro tato rozhraní `null` jsou ukazatele považovány za součást správného chování VSPackage a není vrácena žádná chyba.

 Vzhledem k tomu, že modul CLR nepovoluje, aby byla hodnota parametru [out] `null` , součástí navrženého chování těchto rozhraní není přímo k dispozici ve spravovaném kódu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Metody sestavení vzájemné spolupráce pro ovlivněná rozhraní řeší problém definováním relevantních parametrů jako pole, protože modul CLR umožňuje předávání `null` polí.

 Spravované implementace těchto metod by měly vložit `null` pole do parametru, pokud není nic vráceno. V opačném případě vytvořte pole s jedním prvkem správného typu a vložte vrácenou hodnotu do pole.

 Spravované metody, které přijímají informace z rozhraní s nepovinnými parametry [out] obdrží parametr jako pole. Pouze prověřte hodnotu prvního prvku pole. Pokud není `null` , považovat první prvek, jako by to byl původní parametr.

## <a name="passing-constants-in-pointer-parameters"></a>Předávání konstant v parametrech ukazatele
 Vyhledejte parametry, které jsou definovány jako [in] ukazatelů v rozhraní modelu COM, které jsou definovány jako <xref:System.IntPtr> typ v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypu metody sestavení Interop.

 K podobnému problému dochází, když rozhraní COM předá speciální hodnotu, například 0,-1 nebo-2, místo ukazatele na objekt. Na rozdíl od [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] , modul CLR nepovoluje, aby byly konstanty přetypování jako objekty. Místo toho [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] definiční sestavení definuje parametr jako <xref:System.IntPtr> typ.

 Spravované implementace těchto metod by měly využít skutečnost, že <xref:System.IntPtr> Třída má obojí `int` a `void *` konstruktory pro vytvoření <xref:System.IntPtr> z objektu nebo celočíselné konstanty (podle potřeby).

 Spravované metody, které přijímají <xref:System.IntPtr> parametry tohoto typu, by měly použít <xref:System.IntPtr> operátory převodu typu pro zpracování výsledků. Nejprve převeďte <xref:System.IntPtr> na `int` a otestujte pomocí relevantních celočíselných konstant. Pokud se žádné hodnoty neshodují, převeďte je na objekt požadovaného typu a pokračujte.

 Příklady naleznete v tématech <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .

## <a name="ole-return-values-passed-as-out-parameters"></a>Návratové hodnoty OLE předané jako parametry [out]
 Vyhledejte metody, které mají `retval` vrácenou hodnotu v rozhraní modelu COM, ale mají `int` vrácenou hodnotu a další parametr [out] v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypu metody sestavení Interop. Mělo by být jasné, že tyto metody vyžadují speciální zpracování, protože [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototypy metody sestavení Interop mají jeden další parametr než metody rozhraní modelu COM.

 Mnoho rozhraní COM, která se týkají aktivity OLE, odesílají informace o stavu OLE zpět volajícímu programu uloženému v `retval` návratové hodnotě rozhraní. Namísto použití návratové hodnoty, odpovídající [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metody sestavení vzájemné spolupráce odesílají informace zpět volajícímu programu uloženému v parametru pole [out].

 Spravované implementace těchto metod by měly vytvořit pole s jedním prvkem stejného typu jako parametr [out] a umístit ho do parametru. Hodnota prvku pole by měla být stejná jako odpovídající model COM `retval` .

 Spravované metody, které volají rozhraní tohoto typu, by měly načíst první prvek z pole [out]. Tento element lze zacházet, jako by šlo o `retval` návratovou hodnotu z odpovídajícího rozhraní modelu COM.

## <a name="see-also"></a>Viz také
- [Spolupráce s nespravovaným kódem](/dotnet/framework/interop/index)
