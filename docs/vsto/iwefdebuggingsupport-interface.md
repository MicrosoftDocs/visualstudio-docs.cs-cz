---
title: Rozhraní IWefDebuggingSupport –
description: Přečtěte si, jak můžete pomocí ladicího prostředí, jako je Visual Studio, usnadnit ladění systém Microsoft Officech aplikací.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6a818973bdc2f62194d6ed0026c0798806fe5f2a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525318"
---
# <a name="iwefdebuggingsupport-interface"></a>Rozhraní IWefDebuggingSupport –
  Implementováno ladicím prostředím, jako je například sada Visual Studio, pro usnadnění ladění aplikací pro Office. Aplikace Office, jako je Word nebo Excel, získá toto rozhraní ze sady Visual Studio a potom v rámci relace ladění zavolá metody v rozhraní v určitých okamžicích.

## <a name="syntax"></a>Syntax

```csharp
[
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),
    oleautomation
]
interface IWefDebuggingSupport : IUnknown
{
    HRESULT SetWefProcessId(
        [in] DWORD dwProcessId);
    HRESULT GetAutoInsertExtensions(
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);
}
```

## <a name="methods"></a>Metody
 V následující tabulce jsou uvedeny metody, které definuje rozhraní IWefDebuggingSupport –.

|Název|Popis|
|----------|-----------------|
|[Metoda Getautoinsertextensions –](../vsto/getautoinsertextensions-method.md)|Načte informace o aplikacích pro Office, které se mají automaticky vkládat během ladění.|
|[Metoda Setwefprocessid –](../vsto/setwefprocessid-method.md)|Poskytuje identifikátor procesu, který spustí obsah architektury Web Extensions (WEF).|
