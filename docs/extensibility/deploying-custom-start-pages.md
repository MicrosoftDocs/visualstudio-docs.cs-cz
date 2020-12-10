---
title: Nasazení vlastních stránek Start | Microsoft Docs
description: Naučte se, jak nasadit vlastní úvodní stránky pomocí nasazení VSIX nebo zkopírováním souborů do správných umístění na cílovém počítači.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 76c2fc23a2b76b48152a4d3d44d687f165abf106
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993884"
---
# <a name="deploy-custom-start-pages"></a>Nasazení vlastních spouštěcích stránek

Vlastní úvodní stránky můžete nasadit pomocí nasazení VSIX nebo zkopírováním souborů do správných umístění na cílovém počítači.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Nasazení VSIX pomocí šablony projektu úvodní stránky

Když vytvoříte úvodní stránku pomocí šablony projektu úvodní stránka a potom sestavíte projekt, Visual Studio vytvoří soubor *. vsix* , který můžete distribuovat. Sbalení úvodní stránky v souboru *VSIX* nabízí následující možnosti nasazení v závislosti na zamýšlené cílové skupině:

- Soubor *. vsix* lze umístit do síťové sdílené složky nebo na veřejném webu. Když někdo otevře soubor, automaticky se nainstaluje Úvodní stránka.

- Soubor *. vsix* můžete nahrát na web [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , aby ho uživatelé mohli nainstalovat pomocí **Správce rozšíření**.

Šablona projektu úvodní stránky vytvoří kopii výchozí úvodní stránky sady Visual Studio, abyste mohli upravit kopii a zachovat původní nastavení.

Šablonu projektu úvodní stránky můžete získat pomocí **Správce rozšíření** nebo stažením z webu.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Nasazení VSIX bez použití šablony projektu úvodní stránka
 Úspěšné nasazení VSIX vyžaduje, aby bylo nainstalované rozšíření ve složkách, které rozpozná proces registrace VSIX a **Správce rozšíření**. Vzhledem k tomu, že šablona projektu úvodní stránky již určuje správné složky, doporučujeme ji použít vždy, když chcete zabalit rozšíření pro nasazení VSIX. Pokud ale máte případ, ve kterém šablonu nemůžete použít, můžete vytvořit nasazení VSIX bez jeho použití.

 Chcete-li vytvořit nasazení VSIX bez použití šablony projektu úvodní stránka, nejprve vytvořte soubor *. vsix* pro úvodní stránku jedním z těchto dvou způsobů:

- Přidáním vlastních souborů úvodní stránky do prázdného projektu VSIX. Další informace naleznete v tématu [Šablona projektu VSIX](../extensibility/vsix-project-template.md).

- Ručním vytvořením souboru *. vsix* . Chcete-li vytvořit soubor *. vsix* ručně:

   1. Vytvořte soubor *extension. vsixmanifest* a soubor *[Content_Types]. XML* v nové složce. Další informace naleznete v tématu [anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md).

   2. V Průzkumníku Windows klikněte pravým tlačítkem na složku, která obsahuje dva soubory XML, klikněte na **Odeslat do** a pak klikněte na Komprimovaná složka (ZIP). Přejmenujte výsledný soubor *. zip* na *filename. vsix*, kde filename je název redistribuovatelného souboru, který nainstaluje balíček.

Aby sada Visual Studio rozpoznala úvodní stránku, `Content Element` manifest VSIX musí obsahovat a `CustomExtension Element` , který má `Type` atribut nastaven na `"StartPage"` . Přípona úvodní stránky, která byla nainstalována pomocí nasazení VSIX, se zobrazí v seznamu **Přizpůsobit úvodní stránku** na stránce možnosti **spuštění** jako *název rozšíření* **[installed Extension]** .

Pokud balíček úvodní stránky obsahuje sestavení, je nutné přidat registraci cesty vazby, aby byly k dispozici při spuštění sady Visual Studio. Pokud to chcete provést, ujistěte se, že balíček obsahuje soubor *. pkgdef* , který obsahuje následující informace.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Nasazení VSIX pro všechny uživatele
 Ve výchozím nastavení jsou rozšíření nasazená v balíčcích VSIX nainstalována pouze pro aktuálního uživatele. Můžete vytvořit instalaci úvodní stránky pro všechny uživatele cílového počítače tím, že vytvoříte nasazení All-Users.

### <a name="to-create-an-all-users-deployment"></a>Vytvoření nasazení All-Users

1. Otevřete soubor *extension. vsixmanifest* v zobrazení kódu.

2. V `Identifier` elementu manifestu VSIX přidejte `AllUsers` element, který má hodnotu `true` .

    ```
    <AllUsers>true</AllUsers>
    ```

     To způsobí, že instalační program VSIX vyzve k zadání oprávnění správce a pak nainstaluje soubory do *\Common7\IDE\Extensions*.

3. Otevřete soubor *. pkgdef* .

4. Úpravou souboru *. pkgdef* nastavte výchozí počáteční stránku v klíči HKLM přidáním následujícího, kde *MyStartPage. XAML* je název souboru *. XAML* , který obsahuje úvodní stránku.

     [$RootKey $ \StartPage\Default]

     "URI" = "$PackageFolder $ \\ *MyStartPage. XAML*"

     Tím se aplikaci Visual Studio ukáže, že se bude hledat v novém umístění úvodní stránky.

## <a name="file-copy-deployment"></a>Nasazení kopírování souborů
 K nasazení vlastní úvodní stránky není nutné vytvářet soubor *. vsix* . Místo toho můžete zkopírovat kód a podpůrné soubory přímo do <em>složky \StartPages uživatele \* . V seznamu **Přizpůsobit úvodní stránku</em>* na stránce možnosti **spuštění** jsou uvedeny všechny soubory *. XAML* v této složce společně s cestou, například *%USERPROFILE%\My Documents\Visual Studio {version} \StartPages \\ {File Name}. XAML*. Pokud Úvodní stránka obsahuje odkazy na soukromá sestavení, je nutné je zkopírovat a vložit do složky * \PrivateAssemblies \* .

 Chcete-li distribuovat úvodní stránku, kterou jste vytvořili bez jejich balení v souboru *VSIX* , doporučujeme použít základní strategii kopírování souborů, například skript Batch nebo jakoukoli jinou technologii nasazení, která vám umožní umístit soubory do požadovaných adresářů.

### <a name="to-manually-install-a-custom-start-page"></a>Ruční instalace vlastní úvodní stránky

1. Zkopírujte soubor *. XAML* , který obsahuje značku úvodní stránky, spolu s dalšími podpůrnými soubory než sestaveními a vložte je do složky * \StartPages uživatele \* .

2. Pokud Úvodní stránka vyžaduje sestavení, zkopírujte je a vložte do *.. \\ {Instalační složka sady Visual Studio} \\ \Common7\IDE\PrivateAssemblies*.

3. V seznamu **Přizpůsobit úvodní stránku** na stránce možnosti **spuštění** vyberte novou úvodní stránku. Další informace najdete v tématu [přizpůsobení úvodní stránky](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Viz také

- [Přizpůsobení úvodní stránky](../ide/customizing-the-start-page-for-visual-studio.md)
- [Přidání uživatelského ovládacího prvku na úvodní stránku](../extensibility/adding-user-control-to-the-start-page.md)
