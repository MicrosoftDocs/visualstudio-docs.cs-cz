---
title: Referenční dokumentace schématu 2,0 pro jazykové sady VSIX | Microsoft Docs
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: zorio
author: zoeyr
manager: jillfra
ms.openlocfilehash: f97fd5aee27cdc97cf6eb5731da9fad9cb999e18
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78169336"
---
# <a name="vsix-language-pack-schema-20-reference"></a>Referenční dokumentace schématu 2,0 pro jazykové sady VSIX

Schéma jazykové sady VSIX poskytuje lokalizované informace o instalaci balíčků VSIX. Verze 2,0 tohoto schématu podporuje další prvky lokalizace.

## <a name="language-pack-schema"></a>Schéma jazykové sady

Kořenový prvek souboru jazykové sady je `<PackageLanguagePackManifest>`s atributem `Version`, který je verze formátu jazykové sady. Tento článek popisuje verzi 2,0 formátu jazykové sady, která je zadána v manifestu nastavením atributu `Version` na hodnotu `Version="2.0.0"`. Kořenový element obsahuje přesně jeden podřízený `<Metadata>` element.

### <a name="packagelanguagepackmanifest-element"></a>Element PackageLanguagePackManifest

V elementu `<PackageLanguagePackManifest>` musí existovat následující element:

|Název|Popis|
|-----------|-----------------|
|`<Metadata>`| Nadřazený element pro všechna lokalizovaná metadata balíčku

### <a name="metadata-element"></a>Element metadata

V rámci prvku `<Metadata>` můžete mít následující prvky:

|Název|Popis|
|-----------|-----------------|
|`<DisplayName>`|Lokalizovaný název rozšíření, které se má nainstalovat|
|`<Description>`|Lokalizovaný popis rozšíření, které se má nainstalovat|
|`<License>`| Cesta k lokalizované verzi licence rozšíření|
|`<MoreInfo>`| Odkaz na lokalizované informace o rozšíření|
|`<ReleaseNotes>`| Cesta nebo odkaz na lokalizovanou verzi poznámky k verzi|
|`<Icon>`| Cesta k lokalizované verzi ikony rozšíření|

### <a name="sample-manifest"></a>Vzorový manifest

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

|Název|Popis|
|-----------|-----------------|
|[Lokalizace balíčků VSIX](../extensibility/localizing-vsix-packages.md)|Ukazuje, jak poskytnout lokalizovanou podporu instalace balíčku VSIX.|
|[Referenční dokumentace schématu rozšíření VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)|Manifest VSIX popisuje obsah souboru nasazení *. vsix* . Soubor nasazení umožňuje nainstalovat rozšíření sady Visual Studio pomocí dialogového okna **rozšíření a aktualizace** .|
|[Vyhledání a používání rozšíření sady Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Ukazuje, jak použít dialogové okno **rozšíření a aktualizace** k instalaci, odebrání, aktivaci a deaktivaci rozšíření.|
