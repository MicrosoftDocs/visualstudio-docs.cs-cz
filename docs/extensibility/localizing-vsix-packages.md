---
title: Lokalizace balíčků VSIX | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 54de0b219eb1c86a413b7a95e87a48e7f65ac9ec
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636971"
---
# <a name="localizing-vsix-packages"></a>Lokalizace balíčků VSIX

Je možné lokalizovat VSIX balíček vytvořením *Extension.vsixlangpack* souboru pro každý cílový jazyk a umístit je do správné složky. Při instalaci balíčku lokalizované lokalizovaný název rozšíření se zobrazí spolu s lokalizovaný popis. Pokud zadáte lokalizované licenčního souboru nebo adresu URL, která odkazuje na lokalizované informace, jsou také zobrazeny.

Pokud obsah obsahuje VSIX balíček VSPackage, která přidá příkazy nabídky nebo jiný prvek uživatelského rozhraní, přečtěte si téma [lokalizace příkazů nabídky](../extensibility/localizing-menu-commands.md) informace o lokalizaci nových prvků uživatelského rozhraní.

## <a name="directory-structure"></a>Adresářová struktura

 Když uživatel nainstaluje rozšíření, **rozšíření a aktualizace** kontroluje nejvyšší úrovni balíčku VSIX pro složku, jejíž název odpovídá národní prostředí sady Visual Studio na cílovém počítači. Pokud **rozšíření a aktualizace** najde *.vsixlangpack* souboru ve složce, nahradí jej lokalizované hodnoty v tomto souboru pro odpovídající hodnoty v *.vsixmanifest*souboru. Tyto hodnoty se zobrazí, když se instaluje rozšíření. Následující příklad ukazuje strukturu adresáře pro balíček VSIX, který je lokalizován do Španělština (es-ES) a Francouzština (fr-FR).  

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> Šablony projektů VSIX podporované v [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] generování manifestu VSIX a pojmenujte ho *source.extension.vsixmanifest*. Když Visual Studio vytvoří projekt, zkopíruje obsah tohoto souboru do Extension.VsixManifest v balíčku souboru VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Soubor Extension.vsixlangpack

*Extension.vsixlangpack* souboru způsobem [VSIX Language Pack schema 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Toto schéma je `PackageLanguagePackManifest`, který je okamžitě následován `Metadata` podřízený element. Metadata element může obsahovat až 6 podřízené prvky `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, a `Icon`. Tyto podřízené prvky odpovídají `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, a `Icon` podřízených elementů `Metadata` elementu *Extension.vsixmanifest*souboru.

Když vytvoříte soubor vsixlangpack, je nutné nastavit `Include in Vsix` vlastnost `true`. V opačném případě lokalizovaného instalačního text se bude ignorovat.

### <a name="to-set-the-include-in-vsix-property"></a>Chcete-li nastavit zahrnutí ve vlastnosti Vsix

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor Extension.vsixlangpack a pak klikněte na tlačítko **vlastnosti**.

2.  V **mřížky vlastností**, klikněte na tlačítko **zahrnout do Vsix**a přiřadíte jí hodnotu `true`.

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje příslušné části třídy *Extension.vsixmanifest* souboru. Soubor obsahuje také odpovídající *Extension.vsixlangpack* soubor pro španělštinu. Pokud národní prostředí sady Visual Studio na cílovém počítači je nastaven na španělštinu, nahraďte hodnoty z této jazykové sady hodnot z manifestu.

### <a name="code"></a>Kód

 [*Extension.vsixmanifest*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

 [*Extension.vsixlangpack*]

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>Viz také:

|Název|Popis|
|-----------|-----------------|
|[VSIX Language Pack schema 2.0 odkaz](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Jazykové sady VSIX popisuje informace o lokalizaci nasazení souboru .vsix.|
|[Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Popisuje strukturu a obsah balíčku vsix.|
|[Lokalizace příkazů nabídky](../extensibility/localizing-menu-commands.md)|Ukazuje, jak lokalizovat další prostředky textu v rozšíření.|