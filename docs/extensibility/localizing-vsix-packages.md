---
title: Lokalizace balíčků VSIX | Microsoft Docs
description: Naučte se lokalizovat balíček VSIX vytvořením souboru s příponou. vsixlangpack pro každý cílový jazyk a jejich vložením do správné složky.
ms.custom: SEO-VS-2020
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7d2e297484e89f1ae2cfb9f2be7af25f1fe92714
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073219"
---
# <a name="localizing-vsix-packages"></a>Lokalizace balíčků VSIX

VSIX balíček můžete lokalizovat vytvořením souboru s *příponou. vsixlangpack* pro každý cílový jazyk a jeho vložením do správné složky. Při instalaci lokalizovaného balíčku se lokalizovaný název rozšíření zobrazuje spolu s lokalizovaným popisem. Pokud zadáte lokalizovaný licenční soubor nebo adresu URL, která odkazuje na lokalizované informace, zobrazí se také.

Pokud obsah vašeho balíčku VSIX obsahuje VSPackage, který přidá příkazy nabídky nebo jiné uživatelské rozhraní, přečtěte si téma [lokalizace příkazů nabídky](../extensibility/localizing-menu-commands.md) , kde najdete informace o lokalizaci nových prvků uživatelského rozhraní.

## <a name="directory-structure"></a>Adresářová struktura

 Když uživatel nainstaluje rozšíření, **rozšíření a aktualizace** ověří nejvyšší úroveň balíčku VSIX pro složku, jejíž název se shoduje s národním prostředím sady Visual Studio cílového počítače. Pokud **rozšíření a aktualizace** naleznou soubor *. vsixlangpack* ve složce, nahradí lokalizované hodnoty v tomto souboru odpovídajícími hodnotami v souboru *. vsixmanifest* . Tyto hodnoty se zobrazí při instalaci rozšíření. Následující příklad ukazuje adresářovou strukturu balíčku VSIX, který je lokalizován do španělštiny (ES-ES) a francouzštiny (fr-FR).

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
> Šablony projektů podporované VSIX v [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] manifestu vygenerujte manifest VSIX a pojmenujte ho *source. extension. vsixmanifest*. Když Visual Studio sestaví projekt, zkopíruje obsah tohoto souboru do souboru extension. VsixManifest v balíčku VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Soubor Extension. vsixlangpack

Soubor *extension. vsixlangpack* se řídí [schématem jazykové sady VSIX 2,0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Toto schéma má `PackageLanguagePackManifest` , což je okamžitě následováno `Metadata` podřízeným prvkem. Element metadata může obsahovat až 6 podřízených elementů, `DisplayName` , `Description` , `MoreInfo` , `License` , a `ReleaseNotes` `Icon` . Tyto podřízené prvky odpovídají `DisplayName` `Description` prvkům,, `MoreInfo` , `License` , `ReleaseNotes` a `Icon` podřízeným elementům `Metadata` prvku souboru *extension. vsixmanifest* .

Při vytváření souboru vsixlangpack je nutné nastavit `Include in Vsix` vlastnost na hodnotu `true` . V opačném případě bude lokalizovaný text instalace ignorován.

### <a name="to-set-the-include-in-vsix-property"></a>Nastavení vlastnosti include v souboru VSIX

1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na soubor Extension. vsixlangpack a potom klikněte na příkaz **vlastnosti**.

2. V **mřížce vlastností** klikněte na **zahrnout do VSIX** a nastavte jeho hodnotu na `true` .

## <a name="example"></a>Příklad

### <a name="description"></a>Description

Následující příklad ukazuje relevantní části souboru *extension. vsixmanifest* . Soubor obsahuje také odpovídající soubor *extension. vsixlangpack* pro španělštinu. Hodnoty z jazykové sady nahradí hodnoty z manifestu, pokud je národní prostředí sady Visual Studio cílového počítače nastaveno na španělštinu.

### <a name="code"></a>Kód

- [*Extension. vsixmanifest*]

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

- [*Extension. vsixlangpack*]

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

## <a name="see-also"></a>Viz také

|Nadpis|Popis|
|-----------|-----------------|
|[Referenční dokumentace schématu 2,0 pro jazykové sady VSIX](vsix-language-pack-schema-2-0-reference.md)|Jazyková sada VSIX popisuje informace o lokalizaci souboru nasazení. VSIX.|
|[Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Popisuje strukturu a obsah balíčku VSIX.|
|[Příkazy nabídky lokalizace](../extensibility/localizing-menu-commands.md)|Ukazuje, jak lokalizovat jiné textové prostředky v rozšíření.|
