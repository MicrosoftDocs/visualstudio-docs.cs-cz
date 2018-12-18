---
title: Fragmenty kódu jazyka Visual C# | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snippets [C#], default snippets
- snippets [C#], Code Snippet Inserter
- Code Snippet Inserter [J#]
- Code Snippet Inserter [C#]
- Visual C#, default snippets
ms.assetid: dbea3dd6-e650-4190-b874-c9f097d7de6e
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9c06243b4f41919c1c51002f0ed805a3fbd67112
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49297411"
---
# <a name="visual-c-code-snippets"></a>Fragmenty kódu v jazyce Visual C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fragmenty kódu jsou předdefinované fragmenty kódu, které můžete rychle vkládat do kódu. Například `for` fragment kódu vytvoří prázdnou `for` smyčky. Některé fragmenty kódu jsou příkazu Obklopit s fragmenty kódu, které vám umožní vybrat řádky kódu a klikněte na tlačítko fragment kódu, která zahrnuje vybrané řádky kódu. Například, když vyberete řádků kódu a poté aktivovat `for` fragment kódu vytvoří `for` smyčky s tyto řádky kódu uvnitř smyčka bloku. Fragmenty kódu můžete provést program psaní kódu rychlejší, jednodušší a spolehlivější.  
  
 Můžete vložit fragment kódu do umístění kurzoru nebo vložit obklopit fragmentem kódu kolem vybrané kódu. Vkládací modul fragmentu kódu je vyvolána prostřednictvím **Vložit fragment kódu** nebo **obklopit fragmentem** příkazy na **IntelliSense** nabídce nebo pomocí klávesové zkratky CTRL + K a pak X nebo CTRL + K a potom S v uvedeném pořadí.  
  
 Vkládací modul fragmentu kódu zobrazuje název fragment kódu pro všechny fragmenty kódu k dispozici. Vkládací modul fragmentu kódu také zahrnuje vstupní dialogové okno s typem název fragmentu kódu nebo část názvu fragmentu kódu. Vkládací modul fragmentu kódu zvýrazní nejvíce odpovídá názvu fragmentu kódu. Klávesy TAB kdykoli zrušit Vkládací modul fragmentu kódu a Vložit fragment kódu aktuálně vybraný. Zadáním ESC nebo kliknutím na tlačítko myši v editoru kódu se zavřít Vkládací modul fragmentu kódu bez vložení fragmentu kódu.  
  
## <a name="default-code-snippets"></a>Výchozí fragmenty kódu  
 Ve výchozím nastavení jsou zahrnuty následující fragmenty kódu v sadě Visual Studio.  
  
|Název (nebo místní)|Popis|Platná umístění pro vložení fragmentu kódu|  
|--------------------------|-----------------|---------------------------------------|  
|#if – direktiva|Vytvoří [#if](http://msdn.microsoft.com/library/48cabbff-ca82-491f-a56a-eeccd528c7c2) směrnice a [#endif](http://msdn.microsoft.com/library/6a5fca55-5aee-441f-86f6-1c99fbe9ec05) směrnice.|Kdekoli.|  
|#region – direktiva|Vytvoří [#region](http://msdn.microsoft.com/library/672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4) směrnice a [#endregion](http://msdn.microsoft.com/library/16099660-91b2-49e5-9646-77f9ef069526) směrnice.|Kdekoli.|  
|~|Vytvoří destruktor pro třídu obsahující.|Uvnitř třídy.|  
|– atribut|Vytvoří deklaraci pro třídu, která je odvozena z <xref:System.Attribute>.|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|  
|checked|Vytvoří [zaškrtnutí](http://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|třída|Vytvoří deklaraci třídy.|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|  
|konstruktoru|Vytvoří konstruktor pro třídu obsahující.|Uvnitř třídy.|  
|SH|Vytvoření volání <xref:System.Console.WriteLine%2A>.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|do|Vytvoří [proveďte](http://msdn.microsoft.com/library/50725f79-9ba6-4898-aa78-6e331568a1bb) `while` smyčky.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|else|Vytvoří [else](http://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|enum|Vytvoří [výčtu](http://msdn.microsoft.com/library/bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c) deklarace.|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|  
|equals|Vytvoří deklarace metody, která přepíše <xref:System.Object.Equals%2A> metody definované v <xref:System.Object> třídy.|Uvnitř třídy nebo struktury.|  
|Výjimka|Vytvoří deklaraci pro třídu, která je odvozena z výjimky (<xref:System.Exception> ve výchozím nastavení).|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|  
|pro|Vytvoří [pro](http://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) smyčky.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|foreach|Vytvoří [foreach](http://msdn.microsoft.com/library/5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec) smyčky.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|Díky|Vytvoří [pro](http://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) smyčky této dekrementuje proměnnou smyčky po každé iteraci.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|if|Vytvoří [Pokud](http://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|Indexer|Vytvoří deklaraci indexeru.|Uvnitř třídy nebo struktury.|  
|rozhraní|Vytvoří [rozhraní](http://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba) deklarace.|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|  
|vyvolání|Vytvoří blok, který bezpečně vyvolá událost.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|iterátor|Vytvoří iterátor.|Uvnitř třídy nebo struktury.|  
|iterindex|Vytvoří "s názvem" páru iterátoru a indexer používající vnořenou třídu.|Uvnitř třídy nebo struktury.|  
|lock|Vytvoří [Zámek](http://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|mbox|Vytvoření volání <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName>. Budete muset přidat odkaz na System.Windows.Forms.dll.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|– obor názvů|Vytvoří [obor názvů](http://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f) deklarace.|V oboru názvů (včetně globálního oboru názvů).|  
|Prop|Vytvoří [automaticky implementované vlastnosti](http://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) deklarace.|Uvnitř třídy nebo struktury.|  
|propfull|Vytvoří deklaraci vlastnosti get a přístupové objekty set.|Uvnitř třídy nebo struktury.|  
|propg|Vytvoří jen pro čtení [automaticky implementované vlastnosti](http://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) s privátní přístupový objekt "set".|Uvnitř třídy nebo struktury.|  
|Správce bitových kopií|Vytvoří [statické](http://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[int](http://msdn.microsoft.com/library/212447b4-5d2a-41aa-88ab-84fe710bdb52) deklarace metody Main.|Uvnitř třídy nebo struktury.|  
|struct |Vytvoří [struktura](http://msdn.microsoft.com/library/ff3dd9b7-dc93-4720-8855-ef5558f65c7c) deklarace.|Uvnitř oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|  
|svm|Vytvoří [statické](http://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)[void](http://msdn.microsoft.com/library/0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4) deklarace metody Main.|Uvnitř třídy nebo struktury.|  
|– přepínač|Vytvoří [přepnout](http://msdn.microsoft.com/library/44bae8b8-8841-4d85-826b-8a94277daecb) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|Zkuste|Vytvoří [bloku try-catch](http://msdn.microsoft.com/library/cb5503c7-bfa1-4610-8fc2-ddcd2e84c438) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|tryf|Vytvoří [try-finally](http://msdn.microsoft.com/library/c27623fb-7261-4464-862c-7a369d3c8f0a) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|unchecked|Vytvoří [Nekontrolovaná](http://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|unsafe|Vytvoří [nebezpečné](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) bloku.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
|používání|Vytvoří [pomocí](http://msdn.microsoft.com/library/b42b8e61-5e7e-439c-bb71-370094b44ae8) směrnice.|V oboru názvů (včetně globálního oboru názvů).|  
|while|Vytvoří [při](http://msdn.microsoft.com/library/72a0765c-6852-4aca-b327-4a11cb7f5c59) smyčky.|Uvnitř metoda, indexer, přistupující objekt vlastnosti nebo přístupový objekt události.|  
  
## <a name="see-also"></a>Viz také  
 [Funkce fragmentu kódu](../ide/code-snippet-functions.md)   
 [Fragmenty kódu](../ide/code-snippets.md)   
 [Postupy: vytvoření nové fragment kódu s náhradou](http://msdn.microsoft.com/en-us/8d56d43c-097a-475b-aa85-cae1554b6338)   
 [Parametry šablony](../ide/template-parameters.md)   
 [Postupy: použití příkazu Obklopit s fragmenty kódu](../ide/how-to-use-surround-with-code-snippets.md)   
 [Postupy: Obnovení fragmentů kódu refaktoringu jazyka C#](../ide/how-to-restore-csharp-refactoring-snippets.md)



