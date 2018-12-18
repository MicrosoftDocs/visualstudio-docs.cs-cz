---
title: Nasazení vlastních úvodních stránek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 81b4fb4938c1b87f4a9ca31cdc6035c4c6f124d1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926459"
---
# <a name="deploy-custom-start-pages"></a>Nasazení vlastní úvodní stránky

Vlastní úvodní stránky můžete nasadit pomocí nasazení VSIX nebo kopírování souborů do správných umístění na cílovém počítači.

## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Nasazení souboru VSIX pomocí šablony projektu úvodní stránka

Při vytváření úvodní stránku pomocí šablony projektu úvodní stránky a následné sestavení projektu, Visual Studio vytvoří *VSIX* souborů, které můžete distribuovat. Úvodní stránka v balení *VSIX* souboru poskytuje následující možnosti pro nasazení, v závislosti na vaší zamýšlenou cílovou skupinou:

-   Můžete umístit *VSIX* souboru do sdílené síťové složky nebo na veřejný web. Když uživatel otevře soubor, je automaticky nainstalován úvodní stránky.

-   Můžete nahrát *VSIX* do souboru [galerii sady Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) webu tak, aby uživatelé mohou nainstalovat s použitím **Správce rozšíření**.

Úvodní stránka šablony projektu vytvoří kopii výchozí úvodní stránku aplikace Visual Studio tak, aby mohli upravit kopii a zachovat původní.

Šablona projektu úvodní stránku lze získat pomocí **Správce rozšíření** nebo stažením z webu.

## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>VSIX nasazení bez použití šablony projektu úvodní stránka
 Úspěšné nasazení VSIX vyžaduje rozšíření má být nainstalován do složky, které jsou rozpoznány procesem registrace VSIX a tím **Správce rozšíření**. Vzhledem k tomu, že šablona projektu úvodní stránka již Určuje správné složky, doporučujeme použít ho pokaždé, když chcete balíček rozšíření VSIX nasazení. Nicméně pokud máte případ, ve kterém nelze použít šablonu, můžete vytvořit nasazení VSIX bez jeho použití.

 K vytvoření VSIX nasazení bez použití šablony projektu úvodní stránku, nejprve vytvořte *VSIX* soubor úvodní stránky v některém z těchto způsobů:

- Přidáním vlastní úvodní stránku soubory do prázdný projekt VSIX. Další informace najdete v tématu [šablonou projektu VSIX](../extensibility/vsix-project-template.md).

- Tím, že ručně vytvoříte *VSIX* souboru. Chcete-li vytvořit *VSIX* soubor ručně:

  1.  Vytvořte *extension.vsixmanifest* souboru a *[Content_Types] .xml* souboru do nové složky. Další informace najdete v tématu [anatomie balíčku VSIX](../extensibility/anatomy-of-a-vsix-package.md).

  2.  V Průzkumníku Windows, klikněte pravým tlačítkem na složku, která obsahuje příslušné dva soubory XML, klikněte na tlačítko **odeslat**a potom klikněte na tlačítko komprimovanou složku (metoda ZIP). Přejmenovat výsledný *ZIP* do souboru *Filename.vsix*, kde název_souboru je název redistribuovatelného souboru, který nainstaluje balíček.

  Pro Visual Studio k rozpoznání úvodní stránku `Content Element` musí obsahovat manifestu VSIX `CustomExtension Element` , který má `Type` atribut nastaven na `"StartPage"`. Úvodní stránka rozšíření, nainstalované prostřednictvím VSIX nasazení se zobrazí v **přizpůsobit úvodní stránku** seznamu **spuštění** možnosti stránce jako **[nainstalované rozšíření]** *Název rozšíření*.

  Pokud váš balíček úvodní stránka obsahuje sestavení, je nutné přidat vazbu cesta k registraci tak, aby při spuštění sady Visual Studio jsou k dispozici. Provedete to tak, ujistěte se, že obsahuje balíček *.pkgdef* soubor, který obsahuje následující informace.

```
[$RootKey$\BindingPaths\{Insert a new GUID here}]
"$PackageFolder$"=""
```

### <a name="vsix-deployment-for-all-users"></a>VSIX nasazení pro všechny uživatele
 Ve výchozím nastavení rozšíření, které jsou nasazené do balíčků VSIX nainstalovat pouze pro aktuálního uživatele. Úvodní stránka instalace pro všechny uživatele cílovém počítači můžete díky vytvoření nasazení všech uživatelů.

### <a name="to-create-an-all-users-deployment"></a>Pro vytvoření nasazení všech uživatelů

1.  Otevřít *extension.vsixmanifest* souboru v zobrazení kódu.

2.  V `Identifier` elementu v manifestu vsix, přidejte `AllUsers` element, který má hodnotu `true`.

    ```
    <AllUsers>true</AllUsers>
    ```

     To způsobí, že vsix instalátor výzvu k zadání oprávnění správce a pak nainstalujte soubory, které chcete *\Common7\IDE\Extensions*.

3.  Otevřít *.pkgdef* souboru.

4.  Upravit *.pkgdef* nastavit výchozí úvodní stránky v části HKLM přidáním následujícího kódu, kde *MyStartPage.xaml* je název *.xaml* soubor, který obsahuje vaše spuštění Stránka.

     [$RootKey$ \StartPage\Default]

     "Uri"="$ $PackageFolder\\*MyStartPage.xaml*"

     Znamená to Visual Studio a podívejte se na nové umístění úvodní stránku.

## <a name="file-copy-deployment"></a>Nasazení kopírování souborů
 Není nutné vytvářet *VSIX* uvést pro nasazení vlastní úvodní stránky. Místo toho můžete zkopírovat kód a podpůrné soubory přímo do daného uživatele <em>\StartPages\* složky. **Přizpůsobit úvodní stránku</em>*  seznamu **spuštění** možnosti stránce seznamy každý *.xaml* soubor v této složce, společně s cestu – například *%USERPROFILE%\My Documents\Visual Studio {version} \StartPages\\{název souboru} .xaml*. Pokud vaše úvodní stránka obsahuje odkazy na soukromá sestavení, musí je zkopírujte a vložte je do * \PrivateAssemblies\* složky.

 Pro úvodní stránku, kterou jste vytvořili bez balení v distribuci *VSIX* souborů, doporučujeme použít základní soubor strategie kopírování, například dávkový skript, nebo jiná nasazení technologie, která vám umožní soubory umístit do požadované adresáře.

### <a name="to-manually-install-a-custom-start-page"></a>Pro ruční instalaci vlastní úvodní stránky

1.  Kopírovat *.xaml* soubor, který obsahuje kód, úvodní stránka, spolu s všechny podpůrné soubory jiné než sestavení a vložte je do uživatele * \StartPages\* složky.

2.  Pokud úvodní stránka vyžaduje sestavení, je zkopírujte a vložte je do *... \\{Instalační složky sady visual Studio} \Common7\IDE\PrivateAssemblies\\*.

3.  V **přizpůsobit úvodní stránku** seznamu **spuštění** možnosti vyberte nová úvodní stránka. Další informace najdete v tématu [upravit úvodní stránku](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="see-also"></a>Viz také:

- [Přizpůsobení úvodní stránky](../ide/customizing-the-start-page-for-visual-studio.md)
- [Přidat uživatelský ovládací prvek na úvodní stránku](../extensibility/adding-user-control-to-the-start-page.md)