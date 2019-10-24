---
title: Registrují se obslužné rutiny příkazů sestavení Interop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbc0d162a11df034bec4d1f357ef8abd106da401
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724693"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrace obslužných rutin příkazů definičních sestavení
VSPackage se musí zaregistrovat v [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tak, aby integrované vývojové prostředí (IDE) správně směrují své příkazy.

 Registr lze aktualizovat buď ruční úpravou, nebo pomocí souboru registrátora (. rgs). Další informace najdete v tématu [vytváření skriptů registrátora](/cpp/atl/creating-registrar-scripts).

 Rozhraní Managed Package Framework (MPF) poskytuje tuto funkci prostřednictvím třídy <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute>.

- [Referenční materiály pro formát tabulky příkazů](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) se nacházejí v nespravovaných satelitních knihovnách UI.

## <a name="command-handler-registration-of-a-vspackage"></a>Registrace obslužné rutiny příkazu VSPackage
 VSPackage fungující jako obslužná rutina pro příkazy založené na uživatelském rozhraní (UI) vyžaduje položku registru s názvem po `GUID` VSPackage. Tato položka registru určuje umístění souboru prostředků uživatelského rozhraní VSPackage a prostředku nabídky v tomto souboru. Samotná položka registru se nachází v části HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio \\ *\<Version >* \Menus, kde *\<Version >* je verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], například 9,0.

> [!NOTE]
> Kořenová cesta HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio \\ *\<Version >* lze při inicializaci [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prostředí přepsat alternativním kořenem. Další informace o kořenové cestě najdete v tématu [Instalace VSPackage pomocí Instalační služba systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Položka registru prostředků CTMENU
 Struktura položky registru je:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> je `GUID` VSPackage ve formátu {xxxxxx-XXXX-XXXX-XXXX-XXXXXXXXX}.

 *> informace o \<Resource* se skládá ze tří prvků oddělených čárkami. Tyto prvky jsou, v pořadí:

 \<*cesta k > DLL prostředků*, \<*ID prostředku nabídky*>,*verze nabídky* \< >

 V následující tabulce jsou popsána pole*informace*o \<ch prostředků >.

| Prvek | Popis |
|---------------------------| - |
| \<*cesta k DLL prostředku* > | Toto je úplná cesta k DLL prostředku, která obsahuje prostředek nabídky, nebo je ponecháno prázdné, což značí, že se má použít knihovna DLL prostředků VSPackage (jak je uvedeno v podklíči balíčky, kde je zaregistrována VSPackage).<br /><br /> Pro toto pole nechte toto pole prázdné. |
| *ID prostředku nabídky* \< > | Toto je ID prostředku `CTMENU` prostředku, který obsahuje všechny prvky uživatelského rozhraní pro VSPackage jako kompilované ze souboru [. vsct](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) . |
| *verze nabídky* \< > | Toto je číslo, které se používá jako verze prostředku `CTMENU`. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] používá tuto hodnotu k určení, jestli musí znovu sloučit obsah prostředku `CTMENU` s jeho mezipamětí všech `CTMENU` prostředků. Sloučení se aktivuje spuštěním příkazu pro instalaci nástroje devenv.<br /><br /> Tato hodnota by měla být zpočátku nastavena na 1 a zvýšena po každé změně v prostředku `CTMENU` a před tím, než dojde ke sloučení. |

### <a name="example"></a>Příklad
 Tady je příklad několika položek prostředku:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Viz také:
- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Příkazy a nabídky, které používají spolupracující sestavení](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)