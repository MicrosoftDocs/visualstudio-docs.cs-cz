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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1307d720e005855770ee68659374dbbfae247d65
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541034"
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

 Parametr *bstrManifestURL* obsahuje hodnotu `Manifest` položky v klíči registru **HKEY_CURRENT_USER \software\microsoft\office \\ _\<application name>_ \\ _\<add-in ID>_ \Addins** pro doplněk VSTO. Další informace najdete v tématu [rozhraní IManagedAddin –](../vsto/imanagedaddin-interface.md).

 Implementujte metodu [IManagedAddin –:: Load](../vsto/imanagedaddin-load.md) pro provádění úloh, jako je například konfigurace domény aplikace a zásad zabezpečení pro doplněk VSTO, který se načítá.

## <a name="see-also"></a>Viz také:
- [IManagedAddin – rozhraní](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
