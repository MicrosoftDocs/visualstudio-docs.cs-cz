---
title: '&lt;entryPoint – &gt; element (aplikace ClickOnce) | Microsoft Docs'
description: Element entryPoint identifikuje sestavení, které by mělo být provedeno při spuštění této aplikace ClickOnce v klientském počítači.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5c35d94001ae1e883e2bd76650f248d7e0364d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893890"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;entryPoint – &gt; element (aplikace ClickOnce)
Identifikuje sestavení, které se má provést při [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] spuštění této aplikace v klientském počítači.

## <a name="syntax"></a>Syntax

```xml
<entryPoint
   name
>
   <assemblyIdentity
      name
      version
      processorArchitecture
      language
   />
   <commandLine
      file
      parameters
   />
   <customHostRequired />
   <customUX />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `entryPoint`Element je povinný a je v `urn:schemas-microsoft-com:asm.v2` oboru názvů. `entryPoint`V manifestu aplikace může být definován pouze jeden prvek.

 `entryPoint`Element má následující atribut.

|Atribut|Popis|
|---------------|-----------------|
|`name`|Nepovinný parametr. Tuto hodnotu nepoužívá .NET Framework.|

 `entryPoint` obsahuje následující prvky.

## <a name="assemblyidentity"></a>assemblyIdentity
 Povinná hodnota. Role `assemblyIdentity` a její atributy jsou definovány v [ \<assemblyIdentity> elementu](../deployment/assemblyidentity-element-clickonce-application.md).

 `processorArchitecture`Atribut tohoto prvku a `processorArchitecture` atribut definovaný na `assemblyIdentity` jiném místě v manifestu aplikace se musí shodovat.

## <a name="commandline"></a>Řádek
 Povinná hodnota. Musí být podřízeným `entryPoint` elementu. Nemá žádné podřízené elementy a má následující atributy.

| Atribut | Popis |
|--------------| - |
| `file` | Povinná hodnota. Místní odkaz na sestavení po spuštění pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci. Tato hodnota nemůže obsahovat oddělovače cest lomítka (/) nebo zpětného lomítka ( \\ ). |
| `parameters` | Povinná hodnota. Popisuje akci, která má být provedena s vstupním bodem. Jediná platná hodnota je `run` ; předpokládá se, že je zadán prázdný řetězec `run` . |

## <a name="customhostrequired"></a>customHostRequired
 Nepovinný parametr. Je-li tato možnost k dispozici, určuje, že toto nasazení obsahuje komponentu, která bude nasazena v rámci vlastního hostitele, a není samostatnou aplikací.

 Pokud je tento prvek přítomen, `assemblyIdentity` prvky a `commandLine` nesmí být také k dispozici. Pokud jsou, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] během instalace vyvolá chybu ověřování.

 Tento element nemá žádné atributy a žádné podřízené položky.

## <a name="customux"></a>customUX
 Nepovinný parametr. Určuje, že aplikace je nainstalována a udržována vlastním instalačním programem a nevytváří položku nabídky Start, zástupce nebo přidat nebo odebrat programy.

```xml
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />
```

 Aplikace, která obsahuje element customUX, musí poskytovat vlastní instalační program, který používá <xref:System.Deployment.Application.InPlaceHostingManager> třídu k provádění operací instalace. Aplikaci s tímto elementem nejde nainstalovat dvojitým kliknutím na svůj manifest nebo setup.exe zaváděcího nástroje požadované součásti. Vlastní instalační program může vytvořit položky nabídky Start, zástupce a položky Přidat nebo odebrat programy. Pokud vlastní instalační program nevytvoří položku Přidat nebo odebrat programy, musí uložit identifikátor předplatného poskytnutý <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> vlastností a povolit uživateli odinstalaci aplikace později voláním <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> metody. Další informace naleznete v tématu [Návod: Vytvoření vlastního instalačního programu pro aplikaci ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).

## <a name="remarks"></a>Poznámky
 Tento prvek identifikuje sestavení a vstupní bod pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci.

 Nelze použít `commandLine` k předání parametrů do aplikace v době běhu. Můžete získat přístup k parametrům řetězce dotazu pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] nasazení z aplikace <xref:System.AppDomain> . Další informace naleznete v tématu [How to: načíst informace řetězce dotazu v online aplikaci ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje `entryPoint` prvek v manifestu aplikace pro [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci. Tento příklad kódu je součástí většího příkladu, který je k dispozici v tématu [manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md) .

```xml
<!-- Identify the main code entrypoint. -->
<!-- This code runs the main method in an executable assembly. -->
  <entryPoint>
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
```

## <a name="see-also"></a>Viz také
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)
