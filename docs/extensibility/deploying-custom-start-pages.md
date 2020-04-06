---
title: Nasazení vlastních úvodních stránek | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: 210b4589c0e2165af537c3fa9129affb06197e9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712232"
---
# <a name="deploy-custom-start-pages"></a>Nasazení vlastních úvodních stránek

Vlastní úvodní stránky můžete nasadit pomocí nasazení VSIX nebo zkopírováním souborů do správných umístění v cílovém počítači.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Nasazení VSIX pomocí šablony projektu Úvodní stránka

Když vytvoříte úvodní stránku pomocí šablony projektu Úvodní stránka a potom projekt vytvoříte, Visual Studio vytvoří soubor *.vsix,* který můžete distribuovat. Balení úvodní stránky do souboru *VSix* poskytuje následující možnosti nasazení v závislosti na zamýšlené cílové skupině:

- Soubor *VSIX* můžete umístit do sdílené síťové složky nebo na veřejný web. Když někdo otevře soubor, automaticky se nainstaluje úvodní stránka.

- Soubor *Vsix* můžete nahrát na web [Webu Visual Studio Marketplace,](https://marketplace.visualstudio.com/) aby jej uživatelé mohli nainstalovat pomocí **Správce rozšíření**.

Šablona projektu Úvodní stránka vytvoří kopii výchozí úvodní stránky sady Visual Studio, takže můžete upravit kopii a zachovat originál.

Šablonu projektu Úvodní stránka můžete získat pomocí **Správce rozšíření** nebo ji stažením z webu.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>Nasazení VSIX bez použití šablony projektu Úvodní stránka
 Úspěšné nasazení VSIX vyžaduje rozšíření, které má být nainstalováno ve složkách, které jsou rozpoznány procesem registrace VSIX a **Správcem rozšíření**. Vzhledem k tomu, že šablona projektu Úvodní stránka již určuje správné složky, doporučujeme použít ji vždy, když chcete zabalit rozšíření pro nasazení VSIX. Pokud však máte případ, ve kterém nelze použít šablonu, můžete vytvořit nasazení VSIX bez použití.

 Chcete-li vytvořit nasazení VSIX bez použití šablony projektu Úvodní stránka, nejprve vytvořte soubor *.vsix* pro úvodní stránku jedním z těchto dvou způsobů:

- Přidáním vlastních souborů úvodní stránky do prázdného projektu VSIX. Další informace naleznete [v tématu Šablona projektu VSIX](../extensibility/vsix-project-template.md).

- Ručním vytvořením souboru *.vsix.* Ruční vytvoření souboru *.vsix:*

   1. Vytvořte soubor *hypo.vsixmanifest* a soubor *[Content_Types].xml* v nové složce. Další informace naleznete [v tématu Anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md).

   2. V Průzkumníkovi Windows klikněte pravým tlačítkem myši na složku obsahující dva soubory XML, klikněte na **Odeslat**a potom klikněte na Komprimovaná složka . Přejmenujte výsledný soubor *ZIP* na *Soubor Filename.vsix*, kde Název_souboru je název redistribuovatelného souboru, který nainstaluje váš balíček.

Aby Visual Studio rozpoznalo `Content Element` úvodní stránku, musí `CustomExtension Element` manifest VSIX obsahovat `Type` atribut, který má atribut nastavený na `"StartPage"`. Rozšíření úvodní stránky, které bylo nainstalováno pomocí nasazení VSIX, se zobrazí v seznamu **Přizpůsobit úvodní stránku** na stránce Možnosti **spuštění** jako *název rozšíření* **[Installed Extension]** .

Pokud váš balíček Úvodní stránka obsahuje sestavení, je nutné přidat registraci cesty vazby tak, aby byly k dispozici při spuštění sady Visual Studio. Chcete-li to provést, ujistěte se, že váš balíček obsahuje soubor *.pkgdef,* který obsahuje následující informace.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>Nasazení VSIX pro všechny uživatele
 Ve výchozím nastavení rozšíření nasazené v balíčcích VSIX nainstalovat pouze pro aktuálního uživatele. Můžete provést instalaci úvodní stránky pro všechny uživatele cílového počítače vytvořením nasazení pro všechny uživatele.

### <a name="to-create-an-all-users-deployment"></a>Vytvoření nasazení pro všechny uživatele

1. Otevřete soubor *extension.vsixmanifest* v zobrazení kódu.

2. V `Identifier` elementu manifestu vsix `AllUsers` přidejte prvek, `true`který má hodnotu .

    ```
    <AllUsers>true</AllUsers>
    ```

     To způsobí, že instalační program vsix vyzve k zadání oprávnění správce a potom je nainstaluje do *\Common7\IDE\Extensions*.

3. Otevřete soubor *.pkgdef.*

4. Upravte *.pkgdef* a nastavte výchozí počáteční stránku v hklm přidáním následujícího, kde *MyStartPage.xaml* je název souboru *.xaml,* který obsahuje úvodní stránku.

     [$RootKey$\StartPage\Default]

     "Uri"="$PackageFolder$\\*MyStartPage.xaml*"

     To říká Visual Studio podívat se do nového umístění úvodní stránky.

## <a name="file-copy-deployment"></a>Nasazení kopírování souborů
 K nasazení vlastní úvodní stránky není třeba vytvářet soubor *.vsix.* Místo toho můžete zkopírovat značkovací a podpůrné soubory přímo do <em>složky\* \StartPages uživatele. V seznamu ** Přizpůsobit úvodní stránku</em> * na stránce Možnosti **spuštění** jsou uvedeny všechny soubory *.xaml* v této složce spolu s cestou – například *%USERPROFILE%\Dokumenty\Visual Studio {version}\StartPages\\{Název souboru}.xaml*. Pokud úvodní stránka obsahuje odkazy na soukromá sestavení, musíte je zkopírovat a\* vložit do složky *\PrivateAssemblies.

 Chcete-li distribuovat úvodní stránku, kterou jste vytvořili bez obalu do souboru *.vsix,* doporučujeme použít základní strategii kopírování souborů, například dávkový skript nebo jakoukoli jinou technologii nasazení, která umožňuje umístit soubory do požadovaných adresářů.

### <a name="to-manually-install-a-custom-start-page"></a>Ruční instalace vlastní úvodní stránky

1. Zkopírujte soubor *.xaml,* který obsahuje značky Úvodní stránka, spolu s případnými podpůrnými soubory kromě sestavení\* a vložte je do složky uživatele *\StartPages.

2. Pokud úvodní stránka vyžaduje sestavení, zkopírujte je a vložte je *do .. {Instalační složka sady Visual Studio}\Common7\IDE\PrivateAssemblies\\. \\*

3. V seznamu **Přizpůsobit úvodní stránku** na stránce Možnosti **spuštění** vyberte novou úvodní stránku. Další informace naleznete [v tématu Customize the Start Page](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Viz také

- [Přizpůsobení úvodní stránky](../ide/customizing-the-start-page-for-visual-studio.md)
- [Přidání uživatelského ovládacího prvku na úvodní stránku](../extensibility/adding-user-control-to-the-start-page.md)
