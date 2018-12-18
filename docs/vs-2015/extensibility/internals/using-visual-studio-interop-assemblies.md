---
title: Použití sestavení vzájemné spolupráce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 34
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: df6cee6a2904bd7763f6ae4e18bdd34823ec6c04
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53067551"
---
# <a name="using-visual-studio-interop-assemblies"></a>Používání definičních sestavení sady Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sestavení vzájemné spolupráce pro Visual Studio povolit spravovaným aplikacím přístup k rozhraní modelu COM, které zajistí možnosti rozšíření sady Visual Studio. Existuje několik rozdílů mezi přímo rozhraní COM a jejich vzájemné spolupráce verze. HRESULT – jsou obecně reprezentovány ve formě hodnoty int a je nutné zacházet stejným způsobem jako výjimky a parametry (zejména výstupní parametry) jsou zpracovávat odděleně.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Zpracování výsledky HRESULTs vracené z modelu COM pro spravovaný kód
 Když zavoláte rozhraní modelu COM ze spravovaného kódu, zkontrolujte hodnotu HRESULT a vyvolat výjimku, pokud je to nutné. <xref:Microsoft.VisualStudio.ErrorHandler> Třída obsahuje <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> do něho předaný metodě, která se vyvolá výjimka modelu COM, v závislosti na hodnotu HRESULT.

 Ve výchozím nastavení <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> vyvolá výjimku, pokaždé, když je jí předán HRESULT, který má hodnotu menší než nula. V případech, kdy přípustné hodnoty jsou tyto výsledky HRESULT a měla by být vyvolána žádná výjimka, by měly být předány hodnoty HRESULT Další <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> po otestování hodnoty. Pokud hodnota HRESULT testován odpovídá všechny hodnoty HRESULT explicitně předán <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, není vyvolána žádná výjimka.

> [!NOTE]
>  <xref:Microsoft.VisualStudio.VSConstants> Třída obsahuje konstanty pro běžné HRESULT, například <xref:Microsoft.VisualStudio.VSConstants.S_OK> a <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, a [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] HRESULT, například <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> a <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> poskytuje také <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> a <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> metody, které odpovídají úspěšné a NEÚSPĚŠNÉ makra v modelu COM.

 Zvažte například následující volání funkce, ve kterém <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> je přijatelné vrácení hodnoty, ale jiné HRESULT menší než nula představuje chybu.

 [!code-csharp[VSSDKHRESULTInformation#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]

 Pokud existuje více než jeden přijatelné návratové hodnoty, další hodnoty HRESULT lze připojit pouze k seznamu při volání funkce <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.

 [!code-csharp[VSSDKHRESULTInformation#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Vrací HRESULTS modelu COM ze spravovaného kódu
 Pokud dojde k žádné výjimce, spravovaný kód vrátí <xref:Microsoft.VisualStudio.VSConstants.S_OK> funkce modelu COM, která ji zavolala. Komunikace s objekty COM podporuje běžné výjimky, které jsou silně typované ve spravovaném kódu. Například metoda, která přijímá nepřijatelnou `null` vyvolá argument <xref:System.ArgumentNullException>.

 Pokud si nejste jistí výjimek má vyvolat, ale vy víte HRESULT chcete vrátit do modelu COM, můžete použít <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> metodu pro příslušnou výjimku. Tento postup funguje i s nestandardní chybu, například <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> pokusy o mapování hodnota HRESULT je do něho předaný silného typu výjimky. V případě nedostupnosti vyvolá k obecné výjimce modelu COM. místo. Výsledkem je hodnota HRESULT předání <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> ze spravovaného kódu, které se vrátí do funkce modelu COM, která ji zavolala.

> [!NOTE]
>  Snížit výkon, výjimky, které slouží k označení neobvyklého podmínky. Podmínky, ke kterým dochází často by měla být zpracováván jako vložené, namísto vyvolané výjimky.

## <a name="iunknown-parameters-passed-as-type-void"></a>Parametry IUnknown předány jako typ void**
 Vyhledejte [out] Parametry, které jsou definovány jako typ `void **` v modelu COM rozhraní, ale které jsou definovány jako `[``iid_is``]` v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prototyp metody sestavení vzájemné spolupráce.

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

## <a name="optional-out-parameters"></a>Volitelné [parametry out]
 Vyhledejte parametry, které jsou definovány jako [out] datový typ (`int`, `object`, a tak dále) v modelu COM rozhraní, ale které jsou definovány jako pole stejného datového typu v [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prototyp metody sestavení vzájemné spolupráce.

 Některé COM rozhraní, jako například <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, nakládat [jako volitelné parametry out]. Pokud objekt není povinný, vrátí tato rozhraní COM `null` ukazatele jako hodnotu tohoto parametru místo vytvoření [out] objekt. Jedná se o účel. Pro tato rozhraní `null` ukazatele se předpokládá, že jako součást správné chování sady VSPackage, a není vrácena žádná chyba.

 Protože CLR nepovoluje hodnotu parametr [out] bude `null`, část navrženého chování těchto rozhraní není přímo k dispozici v rámci spravovaného kódu. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Metody sestavení vzájemné spolupráce pro ovlivněné rozhraní tento problém obejít tak, že definujete relevantní parametry jako pole, protože modul CLR umožňuje předat `null` pole.

 Spravované implementace tyto metody by měl umístit `null` pole do parametru, když není nutné nic vrátit. V opačném případě vytvořte pole s jedním prvkem správný typ a vložte návratová hodnota v poli.

 Spravované metody, které se zobrazí informace z rozhraní s volitelné [out] Parametry získávají parametr jako pole. Právě zkontrolujte hodnoty první prvek pole. Pokud není `null`, první prvek zacházet, jako kdyby byly původní parametru.

## <a name="passing-constants-in-pointer-parameters"></a>Předávání konstanty v parametry ukazatele
 Vyhledání parametrů, která jsou definována jako [v] ukazatele rozhraní modelu COM, ale které jsou definovány jako <xref:System.IntPtr> zadejte [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prototyp metody sestavení vzájemné spolupráce.

 K podobnému problému nastane, pokud rozhraní modelu COM předá zvláštní hodnota, například 0, -1 nebo hodnoty – 2, místo ukazatelem na objekt. Na rozdíl od [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], modul CLR neumožňuje konstanty pro přetypování jako objekty. Místo toho [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sestavení vzájemné spolupráce definuje jako parametr <xref:System.IntPtr> typu.

 Spravované implementace z těchto metod zabere fakt, který <xref:System.IntPtr> třídy jsou obě `int` a `void *` konstruktory k vytvoření <xref:System.IntPtr> z objektu nebo celočíselné konstanty, podle potřeby.

 Spravované metody, které přijímají <xref:System.IntPtr> byste použít parametry tohoto typu <xref:System.IntPtr> zadejte operátory převodu ke zpracování výsledků. Nejprve převeďte <xref:System.IntPtr> k `int` a testování proti relevantní celočíselné konstanty. Pokud žádné hodnoty shodují, převeďte jej na objekt požadovaného typu a pokračovat.

 Příklady tohoto objektu, najdete v článku <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.

## <a name="ole-return-values-passed-as-out-parameters"></a>OLE vrátit hodnoty předány jako [parametry out]
 Hledat metody, které mají `retval` vrácená hodnota v rozhraní modelu COM, ale mají `int` vracet hodnotu a zobrazí se další [pole parametrem out] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prototyp metody sestavení vzájemné spolupráce. By mělo být jasné, že tyto metody vyžadují speciální zacházení, protože [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sestavení vzájemné spolupráce metoda prototypy mít jeden parametr více než metody rozhraní modelu COM.

 Mnoho rozhraní modelu COM, které se zabývají OLE aktivity odeslat informace o stavu OLE zpět na volající program uložené v `retval` návratovou hodnotu rozhraní. Namísto použití návratovou hodnotu odpovídající [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] metody sestavení vzájemné spolupráce poslat informace o zpět na volající program uložené v [out] pole parametrů.

 Spravované implementace tyto metody by měly vytvořit pole s jedním prvkem stejného typu jako parametr [out] a vložit ho do parametru. Hodnota prvku pole musí být stejné jako odpovídající COM `retval`.

 Spravované metody, které volají rozhraní tohoto typu by měl vyžádání prvního prvku mimo [out] pole. Tento element lze zacházet, jako by šlo `retval` návratová hodnota z odpovídající rozhraní modelu COM.

## <a name="see-also"></a>Viz také
 [Spolupráce s nespravovaným kódem](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
