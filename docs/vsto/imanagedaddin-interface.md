---
title: IManagedAddin – rozhraní
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IManagedAddin interface
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b436d76164b1744cffe16593149f64d219d04bf1
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541125"
---
# <a name="imanagedaddin-interface"></a>IManagedAddin – rozhraní
  Implementací rozhraní IManagedAddin – Vytvořte komponentu, která načte spravované doplňky VSTO. Toto rozhraní bylo přidáno v 2007 systém Microsoft Office systému.

## <a name="syntax"></a>Syntax

```csharp
[
    object,
    uuid(B9CEAB65-331C-4713-8410-DDDAF8EC191A),
    pointer_default(unique),
    oleautomation
]
interface IManagedAddin : IUnknown
{
    HRESULT Load(
        [in] BSTR bstrManifestURL,
        [in] IDispatch *pdispApplication);
    HRESULT Unload();
};
```

## <a name="methods"></a>Metody
 V následující tabulce jsou uvedeny metody, které jsou definovány rozhraním IManagedAddin –.

|Name|Popis|
|----------|-----------------|
|[IManagedAddin::Load](../vsto/imanagedaddin-load.md)|Volá se, když aplikace systém Microsoft Office načte spravovaný doplněk VSTO.|
|[IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)|Volá se těsně před tím, než aplikace systém Microsoft Office uvolní spravovaný doplněk VSTO.|

## <a name="remarks"></a>Poznámky
 Systém Microsoft Office aplikace, počínaje systém Microsoft Officem systémem 2007, použijte rozhraní IManagedAddin –, které vám pomůžou načíst Doplňky Office VSTO. Rozhraní IManagedAddin – můžete implementovat k vytvoření vlastního zavaděče a modulu runtime doplňku VSTO pro spravované doplňky VSTO místo používání zavaděče doplňku VSTO (*VSTOLoader.dll*) a [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Další informace najdete v tématu [architektura doplňků VSTO](../vsto/architecture-of-vsto-add-ins.md).

## <a name="how-managed-add-ins-are-loaded"></a>Způsob načtení spravovaných doplňků
 Následující kroky se vyskytnou při spuštění aplikace:

1. Aplikace zjišťuje doplňky VSTO tím, že hledá položky v následujícím klíči registru:

    **HKEY_CURRENT_USER \Software\Microsoft\Office \\ *\<application name>* \Addins\\**

    Každá položka v tomto klíči registru je jedinečné ID doplňku VSTO. Obvykle je to název sestavení doplňku VSTO.

2. Aplikace vyhledá `Manifest` položku v položce pro každý doplněk VSTO.

    Spravované doplňky VSTO můžou ukládat úplnou cestu k manifestu v `Manifest` položce **HKEY_CURRENT_USER \software\microsoft\office \\ _\<application name>_ \Addins \\ _\<add-in ID>_ **. Manifest je soubor (obvykle soubor XML), který poskytuje informace, které vám pomůžou při načítání doplňku VSTO.

3. Pokud aplikace najde `Manifest` záznam, aplikace se pokusí načíst spravovanou komponentu zavaděče doplňku VSTO. Aplikace to provede tím, že se pokusí vytvořit objekt modelu COM, který implementuje rozhraní IManagedAddin –.

    [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Zahrnuje komponentu zavaděče doplňku VSTO (*VSTOLoader.dll*), nebo můžete vytvořit vlastní implementací rozhraní IManagedAddin –.

4. Aplikace zavolá metodu [IManagedAddin –:: Load](../vsto/imanagedaddin-load.md) a předá hodnotu `Manifest` položky.

5. Metoda [IManagedAddin –:: Load](../vsto/imanagedaddin-load.md) provádí úlohy vyžadované k načtení doplňku VSTO, jako je například konfigurace domény aplikace a zásad zabezpečení pro doplněk VSTO, který se načítá.

   Další informace o klíčích registru, které systém Microsoft Office aplikace používají ke zjišťování a načítání spravovaných doplňků VSTO, najdete v tématu [položky registru pro doplňky VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

## <a name="guidance-to-implement-imanagedaddin"></a>Pokyny k implementaci IManagedAddin –
 Pokud implementujete IManagedAddin –, je nutné zaregistrovat knihovnu DLL obsahující implementaci pomocí následujícího identifikátoru CLSID:

 99D651D7-5F7C-470E-8A3B-774D5D9536AC

 Systém Microsoft Office aplikace používají tento identifikátor CLSID k vytvoření objektu COM, který implementuje IManagedAddin –.

> [!CAUTION]
> Tento identifikátor CLSID je také používán *VSTOLoader.dll* v [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Proto pokud k vytvoření vlastního zavaděče doplňku VSTO a komponenty prostředí runtime použijete IManagedAddin –, nemůžete tuto komponentu nasadit do počítačů, ve kterých jsou spuštěné doplňky VSTO, které jsou závislé na [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

## <a name="see-also"></a>Viz také
- [Nespravované Reference k rozhraní API &#40;vývoj pro Office v sadě Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)
