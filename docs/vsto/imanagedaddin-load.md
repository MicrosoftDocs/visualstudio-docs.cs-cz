---
title: IManagedAddin::Load
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 605c1dc7a7b0d24ba082767930fd53148cccbd95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920326"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Volá se při načtení spravovaného doplňku VSTO.

## <a name="syntax"></a>Syntaxe

```csharp
HRESULT Load([in] BSTR bstrManifestURL,
             [in] IDispatch *pdispApplication);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*bstrManifestURL*|Úplná cesta k manifestu doplňku VSTO.|
|*pdispApplication*|Ukazatel na rozhraní IDispatch, které představuje hostitelskou aplikaci, která načítá doplněk VSTO.|

## <a name="return-value"></a>Návratová hodnota
 Hodnota HRESULT, která označuje, zda byla metoda úspěšně dokončena.

## <a name="remarks"></a>Poznámky
 Manifest je soubor (obvykle soubor XML), který poskytuje informace, které vám pomůžou při načítání doplňku VSTO. Manifest může například určit umístění sestavení doplňku VSTO a třídu vstupního bodu, která má vytvořit instanci při načtení doplňku VSTO.

 Parametr *bstrManifestURL* obsahuje hodnotu `Manifest` položky v klíči registru **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \Addins \\ _\<add-in ID>_** pro doplněk VSTO. Další informace najdete v tématu [rozhraní IManagedAddin –](../vsto/imanagedaddin-interface.md).

 Implementujte metodu [IManagedAddin –:: Load](../vsto/imanagedaddin-load.md) pro provádění úloh, jako je například konfigurace domény aplikace a zásad zabezpečení pro doplněk VSTO, který se načítá.

## <a name="see-also"></a>Viz také
- [IManagedAddin – rozhraní](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
