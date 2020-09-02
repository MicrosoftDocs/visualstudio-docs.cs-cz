---
title: Registrují se obslužné rutiny příkazů sestavení Interop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e2ab6389f1e0d369dd095290d12c97431c44155
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705865"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrace obslužných rutin příkazů definičních sestavení
VSPackage se musí zaregistrovat v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , aby integrované vývojové prostředí (IDE) správně směrují své příkazy.

 Registr lze aktualizovat buď ruční úpravou, nebo pomocí souboru registrátora (. rgs). Další informace najdete v tématu [vytváření skriptů registrátora](/cpp/atl/creating-registrar-scripts).

 Rozhraní Managed Package Framework (MPF) poskytuje tuto funkci prostřednictvím <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> třídy.

- [Referenční materiály pro formát tabulky příkazů](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) se nacházejí v nespravovaných satelitních knihovnách UI.

## <a name="command-handler-registration-of-a-vspackage"></a>Registrace obslužné rutiny příkazu VSPackage
 VSPackage fungující jako obslužná rutina pro příkazy založené na uživatelském rozhraní (UI) vyžaduje položku registru s názvem po rozhraní VSPackage `GUID` . Tato položka registru určuje umístění souboru prostředků uživatelského rozhraní VSPackage a prostředku nabídky v tomto souboru. Samotná položka registru se nachází v části HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio \\ *\<Version>* \Menus, kde *\<Version>* je verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , například 9,0.

> [!NOTE]
> Kořenovou cestu HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\VisualStudio \\ *\<Version>* lze přepsat alternativním kořenem při [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] inicializaci prostředí shell. Další informace o kořenové cestě najdete v tématu [Instalace VSPackage pomocí Instalační služba systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Položka registru prostředků CTMENU
 Struktura položky registru je:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> je `GUID` ze sady VSPackage ve formátu {xxxxxx-xxxx-xxxx-xxxx-XXXXXXXXX}.

 *\<Resource Information>* se skládá ze tří prvků oddělených čárkami. Tyto prvky jsou, v pořadí:

 \<*Path to Resource DLL*>, \<*Menu Resource ID*>, \<*Menu Version*>

 V následující tabulce jsou popsána pole \<*Resource Information*> .

| Element | Popis |
|---------------------------| - |
| \<*Path to Resource DLL*> | Toto je úplná cesta k DLL prostředku, která obsahuje prostředek nabídky, nebo je ponecháno prázdné, což značí, že se má použít knihovna DLL prostředků VSPackage (jak je uvedeno v podklíči balíčky, kde je zaregistrována VSPackage).<br /><br /> Pro toto pole nechte toto pole prázdné. |
| \<*Menu Resource ID*> | Toto je ID prostředku `CTMENU` prostředku, který obsahuje všechny prvky uživatelského rozhraní pro VSPackage jako kompilované ze souboru [. vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) . |
| \<*Menu Version*> | Toto je číslo, které se používá jako verze pro daný `CTMENU` prostředek. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Tato hodnota používá k určení, jestli musí znovu sloučit obsah `CTMENU` prostředku s jeho mezipamětí všech `CTMENU` prostředků. Sloučení se aktivuje spuštěním příkazu pro instalaci nástroje devenv.<br /><br /> Tato hodnota by měla být zpočátku nastavena na 1 a zvýšena po každé změně v `CTMENU` prostředku a před tím, než dojde ke sloučení. |

### <a name="example"></a>Příklad
 Tady je příklad několika položek prostředku:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Viz také
- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Příkazy a nabídky, které používají definiční sestavení](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
