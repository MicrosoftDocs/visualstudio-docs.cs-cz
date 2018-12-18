---
title: Nasazení vlastních úvodních stránek | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- package start page
- deploy start page
ms.assetid: 4a7eb360-de83-41d5-be53-3cfb160d19f9
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5e788f9bb1ca0333fd20237103cf6bce136af2e0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51795109"
---
# <a name="deploying-custom-start-pages"></a>Nasazení vlastních úvodních stránek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vlastní úvodní stránky můžete nasadit pomocí nasazení VSIX nebo kopírování souborů do správných umístění na cílovém počítači.  
  
## <a name="vsix-deployment-by-using-the-start-page-project-template"></a>Nasazení souboru VSIX pomocí šablony projektu stránka Start  
 Při vytváření úvodní stránku pomocí šablony projektu úvodní stránky a následné sestavení projektu, Visual Studio vytvoří soubor VSIX, které můžete distribuovat. Balení úvodní stránka v souboru .vsix poskytuje následující možnosti pro nasazení, v závislosti na vaše cílová skupina:  
  
- Soubor .vsix lze umístit do sdílené síťové složky nebo na veřejný web. Když uživatel otevře soubor, je automaticky nainstalován úvodní stránky.  
  
- Můžete nahrát soubor .vsix, který má [Galerie sady Visual Studio](http://go.microsoft.com/fwlink/?LinkID=123847) webu tak, aby uživatelé mohou nainstalovat s použitím **Správce rozšíření**.  
  
  Úvodní stránka šablony projektu vytvoří kopii výchozí úvodní stránku aplikace Visual Studio tak, aby mohli upravit kopii a zachovat původní.  
  
  Šablona projektu úvodní stránku lze získat pomocí **Správce rozšíření** nebo stažením z webu.  
  
## <a name="vsix-deployment-without-using-the-start-page-project-template"></a>VSIX nasazení bez použití šablony úvodní stránka projektu  
 Úspěšné nasazení VSIX vyžaduje rozšíření má být nainstalován do složky, které jsou rozpoznány procesem registrace VSIX a tím **Správce rozšíření**. Vzhledem k tomu, že šablona projektu úvodní stránka již Určuje správné složky, doporučujeme použít ho pokaždé, když chcete balíček rozšíření VSIX nasazení. Nicméně pokud máte případ, ve kterém nelze použít šablonu, můžete vytvořit nasazení VSIX bez jeho použití.  
  
 K vytvoření VSIX nasazení bez použití šablony projektu úvodní stránku, nejprve vytvořte soubor VSIX pro úvodní stránku v některém z těchto způsobů:  
  
- Přidáním vlastní úvodní stránku soubory do prázdný projekt VSIX. Další informace najdete v tématu [šablonou projektu VSIX](../extensibility/vsix-project-template.md).  
  
- Tím, že ručně vytvoříte soubor VSIX. Další informace najdete v tématu [postupy: ruční balíček rozšíření (nasazení VSIX)](../misc/how-to-manually-package-an-extension-vsix-deployment.md).  
  
  Pro Visual Studio k rozpoznání úvodní stránku `Content Element` musí obsahovat manifestu VSIX `CustomExtension Element` , který má `Type` atribut nastaven na `"StartPage"`. Úvodní stránka rozšíření, nainstalované prostřednictvím VSIX nasazení se zobrazí v **přizpůsobit úvodní stránku** seznamu **spuštění** možnosti stránce jako **[nainstalované rozšíření]** *Název rozšíření*.  
  
  Pokud váš balíček úvodní stránka obsahuje sestavení, je nutné přidat vazbu cesta k registraci tak, aby při spuštění sady Visual Studio jsou k dispozici. Provedete to tak, ujistěte se, že váš balíček obsahuje soubor .pkgdef, který obsahuje následující informace.  
  
```  
[$RootKey$\BindingPaths\{Insert a new GUID here}]  
"$PackageFolder$"=""  
```  
  
### <a name="vsix-deployment-for-all-users"></a>VSIX nasazení pro všechny uživatele  
 Ve výchozím nastavení rozšíření, které jsou nasazené do balíčků VSIX nainstalovat pouze pro aktuálního uživatele. Úvodní stránka instalace pro všechny uživatele cílovém počítači můžete díky vytvoření nasazení všech uživatelů.  
  
##### <a name="to-create-an-all-users-deployment"></a>Pro vytvoření nasazení všech uživatelů  
  
1.  Otevřete soubor extension.vsixmanifest v zobrazení kódu.  
  
2.  V `Identifier` elementu v manifestu vsix, přidejte `AllUsers` element, který má hodnotu `true`.  
  
    ```  
    <AllUsers>true</AllUsers>  
    ```  
  
     To způsobí, že vsix instalátor výzvu k zadání oprávnění správce a potom nainstalujte soubory \Common7\IDE\Extensions.  
  
3.  Otevřete soubor .pkgdef.  
  
4.  Upravit .pkgdef nastavit výchozí úvodní stránky v části HKLM přidáním následujícího kódu, kde *MyStartPage.xaml* je název souboru XAML, který obsahuje úvodní stránku.  
  
     [$RootKey$ \StartPage\Default]  
  
     "Uri"="$ $PackageFolder\\*MyStartPage.xaml*"  
  
     Říká Visual jednoduchému vás pod rouškou v novém umístění úvodní stránku.  
  
## <a name="file-copy-deployment"></a>Nasazení kopírování souborů  
 Není nutné vytvořit soubor VSIX k nasazení vlastní úvodní stránky. Místo toho můžete zkopírovat kód a podpůrné soubory přímo do složky \StartPages\ uživatele. **Přizpůsobit úvodní stránku** seznamu **spuštění** stránka možností obsahuje seznam každý soubor .xaml v této složce, společně s cestu – například %USERPROFILE%\My Documents\Visual Studio  *verze*\StartPages\\*název_souboru*.xaml. Pokud vaše úvodní stránka obsahuje odkazy na soukromá sestavení, musí je zkopírujte a vložte je do složky \PrivateAssemblies\.  
  
 K distribuci úvodní stránku, kterou jste vytvořili bez balení ho v souboru .vsix, doporučujeme použít strategie kopírování základní soubor, například dávkový skript, nebo jiná nasazení technologie, která vám umožní soubory umístit do požadované adresáře.  
  
#### <a name="to-manually-install-a-custom-start-page"></a>Pro ruční instalaci vlastní úvodní stránky  
  
1.  Soubor .xaml, který obsahuje značky úvodní stránka, spolu s všechny podpůrné soubory jiné než sestavení, zkopírujte a vložte je do složky \StartPages\ uživatele.  
  
2.  Pokud úvodní stránka vyžaduje sestavení, je zkopírujte a vložte je do... \\ *Instalační složky sady visual Studio*\Common7\IDE\PrivateAssemblies\\.  
  
3.  V **přizpůsobit úvodní stránku** seznamu **spuštění** možnosti vyberte nová úvodní stránka. Další informace najdete v tématu [přizpůsobení úvodní stránky](../ide/customizing-the-start-page-for-visual-studio.md).  
  
## <a name="see-also"></a>Viz také  
 [Přizpůsobení úvodní stránky](../ide/customizing-the-start-page-for-visual-studio.md)   
 [Přidání uživatelského ovládacího prvku na úvodní stránku](../extensibility/adding-user-control-to-the-start-page.md)

