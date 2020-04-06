---
title: Registrace obslužných rutin příkazů sestavy interop | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705865"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrace obslužných rutin příkazů definičních sestavení
VSPackage musí zaregistrovat tak, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aby integrované vývojové prostředí (IDE) trasy jeho příkazy správně.

 Registr lze aktualizovat buď ruční úpravou, nebo pomocí souboru registrátora (.rgs). Další informace naleznete [v tématu Vytváření skriptů registrátorů](/cpp/atl/creating-registrar-scripts).

 Architektura spravovaného balíčku (MPF) poskytuje <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> tuto funkci prostřednictvím třídy.

- [Referenční](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) prostředky formátu command table jsou umístěny v nespravovaných satelitních didrecích řízení.

## <a name="command-handler-registration-of-a-vspackage"></a>Registrace obslužné rutiny příkazu balíčku VSPackage
 VSPackage, který funguje jako obslužná rutina příkazů založených na uživatelském `GUID`rozhraní (UI), vyžaduje položku registru pojmenovanou po balíčku VSPackage . Tato položka registru určuje umístění souboru prostředku ui služby VSPackage a prostředku nabídky v rámci tohoto souboru. Samotná položka registru je umístěna pod HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\*\<Version>* \Menus, kde * \<verze>* je verze [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]aplikace , například 9.0.

> [!NOTE]
> Kořenovou cestu HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Version>* lze přepsat alternativním [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] kořenem při inicializování prostředí. Další informace o kořenové cestě naleznete v [tématu Instalace balíčků VSPackages with Installer systému Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>Položka registru prostředků CTMENU
 Struktura položky registru je:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> `GUID` je vbalíčku VSPackage ve tvaru {XXXXXX-XXXX-XXXX-XXXX-XXXXXX-XXXXXXXXX}.

 Informace o zdroji>se skládá ze tří prvků oddělených čárkami. * \<* Tyto prvky jsou v pořadí:

 \<Cesta k> *dll zdroje,* \< *ID prostředku nabídky*>, \<verze *nabídky*>

 V následující tabulce jsou \<popsána pole *informace o prostředku*>.

| Element | Popis |
|---------------------------| - |
| \<*Cesta k dll prostředku*> | Toto je úplná cesta k dll prostředku, který obsahuje prostředek nabídky nebo je ponecháno prázdné, označující, že prostředek VSPackage DLL má být použit (jak je uvedeno v balíček podklíč, kde je registrován v VSPackage sám).<br /><br /> Je obvyklé ponechat toto pole prázdné. |
| \<*ID prostředku nabídky*> | Toto je ID `CTMENU` prostředku, který obsahuje všechny prvky uživatelského rozhraní pro VSPackage zkompilované ze souboru [.vsct.](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) |
| \<*Verze nabídky*> | Toto číslo se používá jako `CTMENU` verze pro prostředek. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Tato hodnota používá k určení, pokud je `CTMENU` třeba zobrazit obsah `CTMENU` prostředku s jeho mezipaměti všech prostředků. Remerge se aktivuje spuštěním příkazu nastavení devenv.<br /><br /> Tato hodnota by měla být zpočátku nastavena na `CTMENU` 1 a po každé změně prostředku a před výskytem remergeu by měla být nastavena na hodnotu 1 a měla by být zpočátku zpříbyná. |

### <a name="example"></a>Příklad
 Zde je příklad několika položek zdrojů:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Viz také
- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Příkazy a nabídky, které používají definiční sestavení](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
