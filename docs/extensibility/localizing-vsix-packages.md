---
title: Lokalizace balíčků VSIX | Dokumenty společnosti Microsoft
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d2d4222e45d56447951e86d558af9983a0d1cc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702901"
---
# <a name="localizing-vsix-packages"></a>Lokalizace balíčků VSIX

Můžete lokalizovat balíček VSIX vytvořením souboru *Extension.vsixlangpack* pro každý cílový jazyk a jejich umístěním do správné složky. Při instalaci lokalizovaného balíčku se zobrazí lokalizovaný název rozšíření spolu s lokalizovaným popisem. Pokud zadáte lokalizovaný licenční soubor nebo adresu URL, která odkazuje na lokalizované informace, zobrazí se také.

Pokud obsah vašeho balíčku VSIX obsahuje VSPackage, který přidává příkazy nabídky nebo jiné uživatelské rozhraní, naleznete informace o lokalizaci nových prvků uživatelského rozhraní v [tématu Localize menu.](../extensibility/localizing-menu-commands.md)

## <a name="directory-structure"></a>Adresářová struktura

 Když uživatel nainstaluje rozšíření, **rozšíření a aktualizace** zkontroluje nejvyšší úroveň balíčku VSIX pro složku, jejíž název odpovídá národní prostředí sady Visual Studio cílového počítače. Pokud **rozšíření a aktualizace** najde soubor *.vsixlangpack* ve složce, nahradí lokalizované hodnoty v tomto souboru odpovídající hodnoty v souboru *.vsixmanifest.* Tyto hodnoty jsou zobrazeny při instalaci rozšíření. Následující příklad ukazuje adresářovou strukturu pro balíček VSIX, který je lokalizován do španělštiny (es-ES) a francouzštiny (fr-FR).

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
> Šablony projektu podporované v six [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] podporované v generovat Manifest VSIX a pojmenujte jej *source.extension.vsixmanifest*. Při visual studio vytvoří projekt, zkopíruje obsah tohoto souboru do Extension.VsixManifest v balíčku VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Soubor Extension.vsixlangpack

Soubor *Extension.vsixlangpack* následuje [schéma jazykové sady VSIX 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Toto schéma má `PackageLanguagePackManifest`, který je bezprostředně `Metadata` následuje podřízený prvek. Prvek Metadata může obsahovat až `DisplayName`6 `Description` `MoreInfo`podřízených prvků , , , `License` `ReleaseNotes`, a `Icon`. Tyto podřízené prvky `Description` `MoreInfo`odpovídají `License` `ReleaseNotes` `DisplayName`, `Icon` , , `Metadata` , a podřízené prvky elementu *souboru Extension.vsixmanifest.*

Při vytváření souboru vsixlangpack je `Include in Vsix` nutné `true`nastavit vlastnost na . V opačném případě bude lokalizovaný text instalace ignorován.

### <a name="to-set-the-include-in-vsix-property"></a>Nastavení vlastnosti Zahrnout do Vsix

1. V **Průzkumníku řešení**klepněte pravým tlačítkem myši na soubor Extension.vsixlangpack a potom klepněte na příkaz **Vlastnosti**.

2. V **mřížce vlastností**klepněte na zahrnout `true`do pole **Vsix**a nastavte její hodnotu na .

## <a name="example"></a>Příklad

### <a name="description"></a>Popis

Následující příklad ukazuje příslušné části souboru *Extension.vsixmanifest.* Soubor také obsahuje odpovídající *soubor Extension.vsixlangpack* pro španělštinu. Hodnoty z jazykové sady nahradit hodnoty ze manifestu, pokud visual studio národní prostředí cílového počítače je nastavena na španělštinu.

### <a name="code"></a>kód

- [*Extension.vsixmanifest*]

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

- [*Extension.vsixlangpack*]

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
|[Odkaz na schéma jazykové sady VSIX 2.0](vsix-language-pack-schema-2-0-reference.md)|Jazyková sada VSIX popisuje informace o lokalizaci souboru nasazení .vsix.|
|[Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Popisuje strukturu a obsah balíčku vsix.|
|[Lokalizovat příkazy nabídky](../extensibility/localizing-menu-commands.md)|Ukazuje, jak lokalizovat jiné textové prostředky v rozšíření.|
