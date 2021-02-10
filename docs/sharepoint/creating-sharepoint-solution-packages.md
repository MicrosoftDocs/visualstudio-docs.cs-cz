---
title: Vytváření balíčků řešení služby SharePoint | Microsoft Docs
description: Vytvářejte a upravujte balíčky pro nasazení pro řešení služby SharePoint pomocí návrháře balíčků. Prozkoumejte nástroje pro balení, možnosti návrháře a strukturu složek.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
- packages [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 423fcaf54d1d46ddf92352f4ff8bdbb637bbe514
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949087"
---
# <a name="create-sharepoint-solution-packages"></a>Vytváření balíčků řešení služby SharePoint
  Pomocí návrháře balíčků můžete vytvořit a přizpůsobit balíčky pro nasazení. Můžete například přidat položky a funkce projektu služby SharePoint, obnovit server služby IIS, nastavit obory aktivace funkcí a identifikovat závislosti funkcí. Návrhář také vygeneruje manifest, soubor XML, který popisuje jednotlivé balíčky.

## <a name="packaging-tools"></a>Nástroje pro balení
 K přizpůsobení balíčku a generování manifestu můžete použít **Návrhář balíčku** . Můžete zahrnout položky projektu služby SharePoint, nakonfigurovat, zda má být webový server resetován, a nastavit typ serveru nasazení. Další informace najdete v tématu [Postup: Přidání a odebrání funkcí a položek do balíčku pomocí návrháře balíčků](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).

 Alternativně můžete pomocí **Průzkumníka balíčků** upravit funkce a položky v souboru balíčku (*. wsp*). Další informace najdete v tématu [Postup: Přidání a odebrání funkcí a položek do balíčku pomocí Průzkumníka balíčků](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

 Pomocí sady Visual Studio a nástroje MSBuild můžete vytvářet soubory balíčku (*. wsp*) k nasazení řešení služby SharePoint. Tento proces generuje soubory manifestu potřebné pro nasazení služby SharePoint. Další informace najdete v tématu [Postup: vytvoření balíčku řešení služby SharePoint pomocí úloh nástroje MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md).

## <a name="package-designer-options"></a>Možnosti návrháře balíčků
 V následující tabulce jsou uvedeny vlastnosti, které lze přizpůsobit v balíčcích služby SharePoint pomocí **nástroje Package Designer**.

|Vlastnost návrháře balíčku|Popis výchozího nastavení|
|-------------------------------|------------------------------------|
|Název|Povinná hodnota. Výchozí název balíčku je nastaven na *ProjectName*.|
|Resetování serveru|Nepovinný parametr. Tuto možnost vyberte, pokud chcete webový server restartovat po instalaci souboru *. wsp* na sharepointovém serveru.|
|Typ serveru nasazení|Nepovinný parametr. Představuje typ serveru, který je hostitelem balíčku. Pokud tato hodnota není nastavená, nastaví se jako výchozí na front-endu.<br /><br /> ApplicationServer: popisuje Server, který hostuje služby.<br /><br /> Webfront-end: popisuje Server, který je hostitelem webů.|
|Položky v řešení|Všechny položky a funkce projektu služby SharePoint, které lze přidat do balíčku.|
|Položky v balíčku|Nepovinný parametr. Všechny položky SharePointu a funkce, které chcete nasadit v balíčku.|

## <a name="configure-the-packaging-process"></a>Konfigurace procesu balení
 Po vývoji řešení služby SharePoint v aplikaci Visual Studio můžete přizpůsobit způsob, jakým jsou projekty zabaleny.

 V následující tabulce jsou uvedeny dva cíle nástroje MSBuild, které lze použít k přizpůsobení způsobu vytvoření souboru *. wsp* .

|Cíl|Description|
|------------|-----------------|
|BeforeLayout|Cíl, který provádí úkoly hned předtím, než se soubory zkopírují do zprostředkujícího adresáře. Soubory můžete upravit před vytvořením souboru balíčku (*. wsp*).|
|AfterLayout|Cíl, který provádí úkoly ihned po zkopírování souborů do zprostředkujícího adresáře.|

 Další informace najdete v tématu [Postup: Přizpůsobení balíčku řešení služby SharePoint pomocí cílů nástroje MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md).

## <a name="packaging-architecture"></a>Architektura balíčku
 Při vytváření balíčku služby SharePoint (*. wsp*) v aplikaci Visual Studio dojde k následujícím krokům.

1. Funkce a balíčky jsou ověřeny, aby se zajistilo, že je fyzická a sémantická struktura balíčku správná.

2. Zobrazí se výčtové funkce, položky projektu a soubory balíčku v balíčku. Soubory manifestu pro balíčky a funkce jsou transformované tak, aby obsahovaly všechny potřebné informace pro nasazení a aktivaci. Tokeny se nahrazují plně kvalifikovanou hodnotou.

3. Je proveden přizpůsobitelný cíl BeforeLayout MSBuild. Tento krok můžete vytvořit, chcete-li provést vlastní úpravy balíčku před vytvořením souboru *. wsp* .

4. Výčtové soubory se zkopírují do zprostředkujícího adresáře.

5. Je proveden přizpůsobitelný cíl AfterLayout MSBuild. Tento krok můžete vytvořit, chcete-li provést vlastní úpravy balíčku před vytvořením souboru *. wsp* .

6. Soubory v zprostředkujícím adresáři se přidají do souboru *. wsp* .

## <a name="package-folder-structure"></a>Struktura složky balíčku
 Po zabalení projektu služby SharePoint se vytvoří soubor *. wsp* pro vás ve složce *SolutionFolder\bin \\ \<BuildConfiguration>* . Například pokud je vaše řešení v *C:\Visual studiu 2013 \ Projects\ListDefinition1* a vaše konfigurace sestavení je nastavená na Release, soubor *. wsp* se nachází v *C:\Visual studiu 2013 \ Projects\ListDefinition1\bin\Release*.

## <a name="see-also"></a>Viz také
- [Postupy: Přizpůsobení balíčku řešení služby SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Postupy: Přidání a odebrání funkcí a položek do balíčku pomocí návrháře balíčků](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
- [Postupy: vytvoření balíčku řešení služby SharePoint pomocí úloh nástroje MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Postupy: vytvoření balíčku řešení služby SharePoint pomocí úloh nástroje MSBuild](../sharepoint/how-to-create-a-sharepoint-solution-package-by-using-msbuild-tasks.md)
- [Postupy: Přizpůsobení balíčku řešení služby SharePoint pomocí cílů nástroje MSBuild](../sharepoint/how-to-customize-a-sharepoint-solution-package-by-using-msbuild-targets.md)
