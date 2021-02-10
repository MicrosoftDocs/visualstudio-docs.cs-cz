---
title: '&lt;trustInfo – &gt; element (aplikace ClickOnce) | Microsoft Docs'
description: Element trustInfo popisuje minimální oprávnění zabezpečení potřebná ke spuštění aplikace v klientském počítači. Element trustInfo je povinný.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#IPermission
- urn:schemas-microsoft-com:asm.v2#PermissionSet
- urn:schemas-microsoft-com:asm.v2#assemblyRequest
- urn:schemas-microsoft-com:asm.v2#trustInfo
- urn:schemas-microsoft-com:asm.v2#defaultAssemblyRequest
- urn:schemas-microsoft-com:asm.v2#security
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- manifests [ClickOnce], trustInfo element
- <trustInfo> element [ClickOnce application manifest]
ms.assetid: 8a813a74-e158-4308-be78-565937f6af83
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3e91bdb2e842692224564374e3f9f4d23cf71cf8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945016"
---
# <a name="lttrustinfogt-element-clickonce-application"></a>&lt;trustInfo – &gt; element (aplikace ClickOnce)
Popisuje minimální oprávnění zabezpečení potřebná ke spuštění aplikace v klientském počítači.

## <a name="syntax"></a>Syntax

```xml

      <trustInfo>
   <security>
      <applicationRequestMinimum>
         <PermissionSet
            ID
            Unrestricted>
            <IPermission
               class
               version
               Unrestricted
            />
         </PermissionSet>
         <defaultAssemblyRequest
            permissionSetReference
         />
         <assemblyRequest
            name
            permissionSetReference
         />
      </applicationRequestMinimum>
      <requestedPrivileges>
         <requestedExecutionLevel
            level
            uiAccess
         />
      </requestedPrivileges>
   </security>
</trustInfo>
```

## <a name="elements-and-attributes"></a>Elementy a atributy
 `trustInfo`Element je povinný a je v `asm.v2` oboru názvů. Nemá žádné atributy a obsahuje následující prvky.

## <a name="security"></a>security
 Povinná hodnota. Tento prvek je podřízeným `trustInfo` prvkem elementu. Obsahuje `applicationRequestMinimum` element a nemá žádné atributy.

## <a name="applicationrequestminimum"></a>applicationRequestMinimum
 Povinná hodnota. Tento prvek je podřízeným `security` prvkem prvku a obsahuje `PermissionSet` `assemblyRequest` prvky, a `defaultAssemblyRequest` . Tento element nemá žádné atributy.

## <a name="permissionset"></a>PermissionSet
 Povinná hodnota. Tento prvek je podřízeným prvkem `applicationRequestMinimum` prvku a obsahuje `IPermission` prvek. Tento element má následující atributy.

- `ID`

     Povinná hodnota. Identifikuje sadu oprávnění. Tento atribut může být libovolná hodnota. Na ID je odkazováno v `defaultAssemblyRequest` `assemblyRequest` atributech a.

- `version`

     Povinná hodnota. Určuje verzi oprávnění. Obvykle je tato hodnota `1` .

## <a name="ipermission"></a>IPermission
 Nepovinný parametr. Tento prvek je podřízeným `PermissionSet` prvkem elementu. `IPermission`Element plně identifikuje třídu oprávnění v .NET Framework. `IPermission`Element má následující atributy, ale může mít další atributy, které odpovídají vlastnostem třídy oprávnění. Chcete-li zjistit syntaxi konkrétního oprávnění, přečtěte si příklady uvedené v souboru Security.config.

- `class`

     Povinná hodnota. Identifikuje třídu oprávnění podle silného názvu. Například následující kód identifikuje `FileDialogPermission` typ.

     `System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

- `version`

     Povinná hodnota. Určuje verzi oprávnění. Tato hodnota je obvykle `1` .

- `Unrestricted`

     Povinná hodnota. Určuje, jestli aplikace potřebuje neomezené udělení tohoto oprávnění. Pokud je `true` udělení oprávnění nepodmíněné. Pokud je `false` , nebo pokud tento atribut není definován, je omezen podle atributů specifických pro oprávnění definovaných na `IPermission` značce. Proveďte následující oprávnění:

    ```xml
    <IPermission
      class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Read="USERNAME" />
    <IPermission
      class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
      version="1"
      Unrestricted="true" />
    ```

     V tomto příkladu deklarace pro <xref:System.Security.Permissions.EnvironmentPermission> omezuje aplikaci pouze na čtení uživatelského jména proměnné prostředí, zatímco deklarace pro <xref:System.Security.Permissions.FileDialogPermission> dává aplikaci neomezený přístup ke všem <xref:System.Windows.Forms.FileDialog> třídám.

## <a name="defaultassemblyrequest"></a>defaultAssemblyRequest
 Nepovinný parametr. Určuje sadu oprávnění udělených pro všechna sestavení. Tento prvek je podřízeným `applicationRequestMinimum` prvkem prvku a má následující atribut.

- `permissionSetReference`

     Povinná hodnota. Určuje ID sady oprávnění, která je výchozím oprávněním. Sada oprávnění je deklarována v `PermissionSet` elementu.

## <a name="assemblyrequest"></a>assemblyRequest
 Nepovinný parametr. Identifikuje oprávnění pro konkrétní sestavení. Tento prvek je podřízeným `applicationRequestMinimum` prvkem prvku a má následující atributy.

- `Name`

     Povinná hodnota. Určuje název sestavení.

- `permissionSetReference`

     Povinná hodnota. Určuje ID sady oprávnění, kterou toto sestavení vyžaduje. Sada oprávnění je deklarována v `PermissionSet` elementu.

## <a name="requestedprivileges"></a>requestedPrivileges
 Nepovinný parametr. Tento prvek je podřízeným prvkem `security` prvku a obsahuje `requestedExecutionLevel` prvek. Tento element nemá žádné atributy.

## <a name="requestedexecutionlevel"></a>requestedExecutionLevel
 Nepovinný parametr. Určuje úroveň zabezpečení, na které aplikace požaduje spuštění. Tento element nemá žádné podřízené položky a má následující atributy.

- `Level`

   Povinná hodnota. Označuje úroveň zabezpečení, kterou aplikace požaduje. Možné hodnoty:

   `asInvoker`, nevyžaduje žádná další oprávnění. Tato úroveň nevyžaduje žádné další výzvy pro vztah důvěryhodnosti.

   `highestAvailable`požaduje nejvyšší oprávnění, která jsou k dispozici nadřazenému procesu.

   `requireAdministrator`, vyžaduje oprávnění úplného správce.

   [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace se nainstalují jenom s hodnotou `asInvoker` . Instalace s jakoukoli jinou hodnotou se nezdaří.

- `uiAccess`

   Nepovinný parametr. Určuje, zda aplikace vyžaduje přístup k prvkům chráněného uživatelského rozhraní. Hodnoty jsou buď `true` nebo `false` , a výchozí hodnota je false. Pouze podepsané aplikace by měly mít hodnotu true.

## <a name="remarks"></a>Poznámky
 Pokud [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace požádá o další oprávnění, než bude klientský počítač ve výchozím nastavení udělovat, bude správce vztahu důvěryhodnosti modulu CLR požádat uživatele, pokud chce aplikaci udělit tuto zvýšenou úroveň důvěryhodnosti. Pokud ne, aplikace se nespustí; v opačném případě se spustí s požadovanými oprávněními.

 Všechna oprávnění vyžadovaná pomocí `defaultAssemblyRequest` a `assemblyRequest` budou udělována bez zobrazení výzvy uživateli, pokud má manifest pro nasazení platnou důvěryhodnou licenci.

 Další informace o zvýšení oprávnění najdete v tématu [zabezpečení aplikací ClickOnce](../deployment/securing-clickonce-applications.md). Další informace o nasazení zásad najdete v tématu [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md).

## <a name="examples"></a>Příklady
 Následující tři příklady kódu ilustrují `trustInfo` prvky pro výchozí pojmenované zóny zabezpečení – Internet, LocalIntranet a FullTrust – pro použití v [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifestu aplikace nasazení.

 První příklad ukazuje `trustInfo` prvek pro výchozí oprávnění dostupná v zóně zabezpečení Internetu.

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="Internet">
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Access="Open" />
          <IPermission
           class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="DomainIsolationByUser"
            UserQuota="10240" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Window="SafeTopLevelWindows"
            Clipboard="OwnClipboard" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="SafePrinting" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="Internet" />
      </applicationRequestMinimum>
    </security>
  </trustInfo>
```

 Druhý příklad ukazuje `trustInfo` prvek pro výchozí oprávnění dostupná v zóně zabezpečení LocalIntranet.

```xml
<trustInfo>
    <security>
      <applicationRequestMinimum>
        <PermissionSet ID="LocalIntranet">
          <IPermission
            class="System.Security.Permissions.EnvironmentPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Read="USERNAME" />
          <IPermission
            class="System.Security.Permissions.FileDialogPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Security.Permissions.IsolatedStorageFilePermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Allowed="AssemblyIsolationByUser"
            UserQuota="9223372036854775807"
            Expiry="9223372036854775807"
            Permanent="True" />
          <IPermission
            class="System.Security.Permissions.ReflectionPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="ReflectionEmit" />
          <IPermission
            class="System.Security.Permissions.SecurityPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Flags="Assertion, Execution" />
          <IPermission
            class="System.Security.Permissions.UIPermission, mscorlib, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Net.DnsPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1"
            Unrestricted="true" />
          <IPermission
            class="System.Drawing.Printing.PrintingPermission, System.Drawing, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
            version="1"
            Level="DefaultPrinting" />
          <IPermission
            class="System.Diagnostics.EventLogPermission, System, Version=1.2.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
            version="1" />
        </PermissionSet>
        <defaultAssemblyRequest permissionSetReference="LocalIntranet" />
      </applicationRequestMinimum>
    </security>
</trustInfo>
```

 Třetí příklad ukazuje `trustInfo` prvek pro výchozí oprávnění dostupná v zóně zabezpečení FullTrust.

```xml
<trustInfo>
  <security>
    <applicationRequestMinimum>
      <PermissionSet ID="FullTrust" Unrestricted="true" />
      <defaultAssemblyRequest permissionSetReference="FullTrust" />
    </applicationRequestMinimum>
  </security>
</trustInfo>
```

## <a name="see-also"></a>Viz také
- [Přehled nasazení důvěryhodných aplikací](../deployment/trusted-application-deployment-overview.md)
- [Manifest aplikace ClickOnce](../deployment/clickonce-application-manifest.md)