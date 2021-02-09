---
title: '&lt;customErrorReporting – &gt; element (nasazení ClickOnce) | Microsoft Docs'
description: Element customErrorReporting Určuje identifikátor URI, který se má zobrazit, když dojde k chybě namísto dialogového okna chyby, ve kterém se zobrazuje zásobník výjimky.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b168b3bcb90ae758609698de306928eb7e13d909
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888482"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting – &gt; element (nasazení ClickOnce)
Určuje identifikátor URI, který se má zobrazit, když dojde k chybě.

## <a name="syntax"></a>Syntax

```xml
<customErrorReporting
   uri
/>
```

## <a name="remarks"></a>Poznámky
 Tento element je volitelný. Bez něho [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zobrazuje dialogové okno chyby zobrazující zásobník výjimky. Pokud `customErrorReporting` je prvek přítomen, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] místo toho zobrazí identifikátor URI, který je označen `uri` parametrem. Cílový identifikátor URI bude obsahovat třídu vnější výjimky, třídu vnitřní výjimky a zprávu vnitřní výjimky jako parametry.

 Tento prvek použijte k přidání funkce zasílání zpráv o chybách do aplikace. Vzhledem k tomu, že vygenerovaný identifikátor URI obsahuje informace o typu chyby, může váš web analyzovat tyto informace a zobrazovat, například příslušnou obrazovku pro řešení problémů.

## <a name="example"></a>Příklad
 Následující fragment kódu ukazuje `customErrorReporting` element spolu s generovaným identifikátorem URI, který může vytvořit.

```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />

Example Generated Error:
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.
```

## <a name="see-also"></a>Viz také
- [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)