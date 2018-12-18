---
title: Publikovat stranu, Návrhář projektů (vývoj pro Office v sadě Visual Studio)
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e4d315a00f527953500b47095ee4080b4eafd4cc
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672714"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Publikovat stranu, Návrhář projektů (vývoj pro Office v sadě Visual Studio)
  **Publikovat** stránku **Návrháře projektu** slouží ke konfiguraci vlastností pro nasazení.  
  
 Pro přístup k této stránce, vyberte projekt v **Průzkumníka řešení**a potom na **projektu** nabídce zvolte *Projectname* **vlastnosti** . Pokud **publikovat** stránka se nezobrazí, zvolte **publikovat** kartu.  
  
> [!NOTE]  
>  Můžete také nastavit umístění pro publikování **Průvodce publikováním**. Další informace najdete v tématu [postupy: publikování řešení Office s použitím technologie ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Umístění složky pro publikování (webový server, ftp server nebo cesta k souboru)**  
 Požadováno.  
  
 Umístění složky pro publikování je adresář, do které Visual Studio kopíruje soubory řešení, jako je například manifesty, sestavení a dalších souborů ze sestavení. Musíte mít přístup pro zápis do tohoto adresáře.  
  
 Mezi možnosti patří v místním počítači, UNC sdílené složky nebo webové stránky HTTP/HTTPS. Cesta může být místní (*c:\foldername\publishfolder*), relativní (*publikovat\\*), nebo plně kvalifikované umístění (*\\\servername\foldername* nebo http://<em>servername/foldername</em>).  
  
 Ve výchozím nastavení, je umístění pro publikování *http://localhost/projectname/* Pokud máte službu IIS nainstalovánu, nebo *publikovat\\*  adresáře, pokud nemáte nainstalovanou službu IIS.  
  
 **Adresa URL složky instalace**  
 Volitelné.  
  
 Adresa URL složky instalace je adresář, ze kterého koncový uživatel nainstaluje vlastního nastavení. Je také cestu pro toto řešení bude používat ke kontrole aktualizací. Cesta může být stejné jako umístění složky pro publikování, ale to není povinné.  
  
 Mezi možnosti patří v místním počítači, UNC sdílené složky nebo webové stránky HTTP/HTTPS. Cesta může být místní (*c:\foldername\publishfolder*), relativní (*publikovat\\*), nebo plně kvalifikované umístění (*\\\servername\foldername* nebo http://<em>servername/foldername</em>). Všechna místa protokolu HTTP/HTTPS musí být vytvořena znaků US-ASCII. Znaky Unicode nejsou podporovány.  
  
 Pokud cesta instalace je nastavena, musí být soubory vlastního nastavení v dané oblasti pro uživatele k instalaci vlastního nastavení. Umístění je třeba nastavit pouze v případě, že znáte umístění poslední nasazení.  
  
 Instalační soubory jsou v umístění vzhledem k dokumentu nebo instalační program, například s možností CD, ponechte toto pole prázdné.  
  
 Tato hodnota lze přiřadit později microsoftem nebo správcem. Další informace najdete v tématu [jak: změnit cestu instalace řešení pro Office](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 **Požadované součásti**  
 Požadavky lze zahrnout pomocí instalačního programu nebo stažen na vyžádání během instalace.  
  
- **Stáhnout nezbytné součásti z webu dodavatele součástí**: tuto možnost použijte, chcete-li stáhnout tyto požadavky od Microsoftu.  
  
- **Stáhnout součásti ze stejného umístění, jako je má aplikace**: tuto možnost použijte, pokud chcete zabalit požadované součásti v instalačním programem vaší. Včetně požadované soubory s instalačním programem zvyšuje velikost řešení.  
  
- **Stáhnout nezbytné součásti z následujícího umístění**: tuto možnost použijte, aby požadavky k dispozici koncovým uživatelům samostatně jako jiný instalační program na webové stránky nebo sdílené síťové složce.  
  
  **Aktualizace**  
  Interval aktualizace Určuje, jak často se řešení zjišťuje dostupnost aktualizací. Ve výchozím nastavení je kontrolovat každých sedm dní.  
  
  Vyhledávají se aktualizace pokaždé, když je načten do přizpůsobení na úrovni dokumentu nebo doplňku VSTO ponechá ho aktualizovat, ale bude mít vliv na výkon při spuštění.  
  
  Pokud provádíte nasazení s použitím disku CD-ROM nebo vyměnitelné jednotky, nastavte tuto vlastnost **nikdy Nezjišťovat dostupnost aktualizací**.  
  
  **Možnosti (popis)**  
  Můžete nastavit možnosti publikovat pro následující vlastnosti:  
  
- Jazyk publikování: národní prostředí řešení pro Office.  
  
- Název vydavatele: název společnosti nebo vývojář se zobrazí v **přidat nebo odebrat programy** nebo **programy a funkce**.  
  
- Název produktu: název řešení Office, protože se zobrazí v **přidat nebo odebrat programy** nebo **programy a funkce**.  
  
- Adresa URL podpory: umístění koncoví uživatelé kontaktovat technickou podporu pro řešení Office.  
  
  **Možnosti (nastavení Office)**  
  Můžete nastavit možnosti publikovat pro následující vlastnosti:  
  
- Název řešení: název jako řešení pro Office se zobrazí v aplikaci Office.  
  
- Popis: popis jako řešení pro Office se zobrazí v aplikaci Office.  
  
- Chování načítání doplňku VSTO.  
  
  -   Při spuštění: Určuje, že doplňku VSTO načte při spuštění aplikace Office.  
  
  -   Načítání na vyžádání: Určuje, že doplňku VSTO načte Pokud aplikace vyžaduje, například když uživatel klikne prvek uživatelského rozhraní, která využívá funkce v doplňku VSTO.  
  
  **Jazyk publikování** tato možnost nastaví jazyk licenční podmínky pro Software společnosti Microsoft a obsahuje seznam požadovaných jazykových sad. Jazyk vlastního nastavení nemá vliv. Jazyk v instalačním programu se určuje podle nainstalované jazyky sady Visual Studio.  
  
  Další informace o tom, jak změnit **jazyk publikování**, naleznete v tématu [postupy: Změna jazyka publikování pro aplikaci ClickOnce](/visualstudio/deployment/how-to-change-the-publish-language-for-a-clickonce-application).  
  
  **Verze publikování**  
  Nastaví číslo verze pro přizpůsobení. Při změně číslo verze aplikace publikována jako aktualizace. Během procesu sestavení, abyste zabránili přepsání dříve publikované verze je vytvořena nová složka pro každou verzi. Každá část verzi publikování (**hlavní**, **menší**, **sestavení**, **revize**) může obsahovat až pět číslic.  
  
  **Automaticky zvyšovat číslo každé vydané verze**  
  Volitelné. Při výběru (výchozí), **revize** část čísla verze se zvýší o jedna pokaždé, když se publikuje přizpůsobení. To způsobí, že má být publikován jako aktualizace vlastního nastavení.  
  
  **Publikovat**  
  Publikuje aplikace s použitím aktuální nastavení. Ekvivalentní **Dokončit** tlačítko **Průvodce publikováním**.  
  
## <a name="see-also"></a>Viz také:  
 [Nasazení řešení Office](../vsto/deploying-an-office-solution.md)   
 [Nasazení řešení Office s použitím technologie ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Požadavky řešení Office na nasazení](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e)  
  
  