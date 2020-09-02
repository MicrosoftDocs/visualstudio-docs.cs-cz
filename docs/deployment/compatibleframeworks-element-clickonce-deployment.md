---
title: '&lt;compatibleFrameworks – &gt; element (nasazení ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <compatibleFrameworks> element [ClickOnce deployment manifest]
ms.assetid: f6c3ee55-9e65-403d-8664-3ebde872c7d4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99db3d51414197df469aaa2eabe97e0967c31b05
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "66746032"
---
# <a name="ltcompatibleframeworksgt-element-clickonce-deployment"></a>&lt;compatibleFrameworks – &gt; element (nasazení ClickOnce)
Identifikuje verze .NET Framework, kde se tato aplikace může nainstalovat a spustit.

> [!NOTE]
> [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client) nepodporuje `compatibleFrameworks` element při ukládání manifestu aplikace, který již byl podepsán pomocí certifikátu pomocí [*MageUI.exe*](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Místo toho je nutné použít [*Mage.exe*](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

## <a name="syntax"></a>Syntax

```xml
<compatibleFrameworks
      SupportUrl> 
   <framework
      targetVersion
      profile
      supportedRuntime
   /> 
</ compatibleFrameworks>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `compatibleFrameworks`Element je vyžadován pro manifesty nasazení, které cílí na [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] modul runtime od .NET Framework 4 nebo novější. `compatibleFrameworks`Element obsahuje jeden nebo více `framework` prvků, které určují .NET Framework verze, na kterých lze tuto aplikaci spustit. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Modul runtime spustí aplikaci na první dostupné `framework` v tomto seznamu.

 V následující tabulce je uveden atribut, který `compatibleFrameworks` podporuje element.

|Atribut|Popis|
|---------------|-----------------|
|`S` `upportUrl`|Nepovinný parametr. Určuje adresu URL, kam lze stáhnout upřednostňovanou kompatibilní verzi .NET Framework.|

## <a name="framework"></a>rozhraní
 Povinná hodnota. V následující tabulce jsou uvedeny atributy, které `framework` prvek podporuje.

|Atribut|Popis|
|---------------|-----------------|
|`targetVersion`|Povinná hodnota. Určuje číslo verze cílového .NET Framework.|
|`profile`|Povinná hodnota. Určuje profil cílového .NET Framework.|
|`supportedRuntime`|Povinná hodnota. Určuje číslo verze modulu runtime přidruženého k cílovému .NET Framework.|

## <a name="remarks"></a>Poznámky

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje `compatibleFrameworks` prvek v [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu nasazení. Toto nasazení může běžet na [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] . Může také běžet na .NET Framework 4, protože je nadmnožinou [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)] .

```xml
<compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">
  <framework
      targetVersion="4.0"
      profile="Client"
      supportedRuntime="4.0.30319" />
</compatibleFrameworks>
```

## <a name="see-also"></a>Viz také
- [ClickOnce – manifest nasazení](../deployment/clickonce-deployment-manifest.md)