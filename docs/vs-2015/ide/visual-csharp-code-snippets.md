---
title: Fragmenty kódu v jazyce Visual C# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- snippets [C#], default snippets
- snippets [C#], Code Snippet Inserter
- Code Snippet Inserter [J#]
- Code Snippet Inserter [C#]
- Visual C#, default snippets
ms.assetid: dbea3dd6-e650-4190-b874-c9f097d7de6e
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fb84854bd871277f680a753b28c17e3429283928
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72646710"
---
# <a name="visual-c-code-snippets"></a>Fragmenty kódu v jazyce Visual C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Fragmenty kódu jsou předem připravené fragmenty kódu, které můžete rychle vložit do kódu. Například `for` fragment kódu vytvoří prázdnou `for` smyčku. Některé fragmenty kódu jsou obklopeny – s fragmenty kódu, které umožňují vybrat řádky kódu a pak vybrat fragment kódu, který zahrnuje vybrané řádky kódu. Například když vyberete řádky kódu a pak aktivujete `for` fragment kódu, vytvoří `for` smyčku s těmito řádky kódu uvnitř bloku smyčky. Fragmenty kódu můžou urychlit psaní kódu programu, jednodušší a spolehlivější.

 Fragment kódu můžete vložit do umístění kurzoru nebo vložit obklopit s fragmentem kódu kolem aktuálně vybraného kódu. Fragment kódu Inserter je vyvolán prostřednictvím příkazu **Vložit fragment kódu** nebo **obklopit** příkazy v nabídce **technologie IntelliSense** nebo pomocí klávesových zkratek CTRL + k a pak X nebo CTRL + K a v uvedeném pořadí.

 Fragment kódu Inserter zobrazí název fragmentu kódu pro všechny dostupné fragmenty kódu. Fragment kódu Inserter také obsahuje vstupní dialogové okno, kde můžete zadat název fragmentu kódu nebo část názvu fragmentu kódu. Fragment kódu Inserter zvýrazňuje nejbližší shodu s názvem fragmentu kódu. Stiskem klávesy TAB kdykoliv dojde k zavření fragmentu kódu Inserter a vložení aktuálně vybraného fragmentu kódu. Zadáním klávesy ESC nebo kliknutím na myš v editoru kódu zavřete fragment kódu Inserter bez vložení fragmentu kódu.

## <a name="default-code-snippets"></a>Výchozí fragmenty kódu
 Ve výchozím nastavení jsou součástí sady Visual Studio následující fragmenty kódu.

|Název (nebo zástupce)|Popis|Platná umístění pro vložení fragmentu|
|--------------------------|-----------------|---------------------------------------|
|#if – direktiva|Vytvoří direktivu [#if](https://msdn.microsoft.com/library/48cabbff-ca82-491f-a56a-eeccd528c7c2) a direktivu [#endif](https://msdn.microsoft.com/library/6a5fca55-5aee-441f-86f6-1c99fbe9ec05) .|Jakékoli.|
|#region – direktiva|Vytvoří direktivu [#region](https://msdn.microsoft.com/library/672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4) a direktivu [#endregion](https://msdn.microsoft.com/library/16099660-91b2-49e5-9646-77f9ef069526) .|Jakékoli.|
|~|Vytvoří destruktor pro třídu, která ji obsahuje.|Uvnitř třídy.|
|– atribut|Vytvoří deklaraci pro třídu, která je odvozena z <xref:System.Attribute> .|V oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|checked|Vytvoří [kontrolovaný](https://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) blok.|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|třída|Vytvoří deklaraci třídy.|V oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|ctor|Vytvoří konstruktor pro třídu, která ji obsahuje.|Uvnitř třídy.|
|Skupina|Vytvoří volání <xref:System.Console.WriteLine%2A> .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|do|Vytvoří [do](https://msdn.microsoft.com/library/50725f79-9ba6-4898-aa78-6e331568a1bb) `while` smyčku do.|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|else|Vytvoří blok [Else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|enum|Vytvoří deklaraci [výčtu](https://msdn.microsoft.com/library/bbeb9a0f-e9b3-41ab-b0a6-c41b1a08974c) .|V oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|equals|Vytvoří deklaraci metody, která přepíše <xref:System.Object.Equals%2A> metodu definovanou ve <xref:System.Object> třídě.|Uvnitř třídy nebo struktury.|
|jímka|Vytvoří deklaraci pro třídu, která je odvozena z výjimky ( <xref:System.Exception> ve výchozím nastavení).|V oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|pro|Vytvoří smyčku [for](https://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|foreach|Vytvoří smyčku [foreach](https://msdn.microsoft.com/library/5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|forr|Vytvoří smyčku [for](https://msdn.microsoft.com/library/34041a40-2c87-467a-9ffb-a0417d8f67a8) , která po každé iteraci sníží proměnnou smyčky.|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|if|Vytvoří blok [if](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|indexer|Vytvoří deklaraci indexeru.|Uvnitř třídy nebo struktury.|
|rozhraní|Vytvoří deklaraci [rozhraní](https://msdn.microsoft.com/library/7da38e81-4f99-4bc5-b07d-c986b687eeba) .|V oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|Zavolejte|Vytvoří blok, který bezpečně vyvolá událost.|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|iterátor|Vytvoří iterátor.|Uvnitř třídy nebo struktury.|
|iterindex|Vytvoří iterátor "pojmenovaný" a dvojici indexeru pomocí vnořené třídy.|Uvnitř třídy nebo struktury.|
|lock|Vytvoří blok [zámku](https://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|mbox|Vytvoří volání <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> . Je možné, že budete muset přidat odkaz na System.Windows.Forms.dll.|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|namespace|Vytvoří deklaraci [oboru názvů](https://msdn.microsoft.com/library/0a788423-9110-42e0-97d9-bda41ca4870f) .|Uvnitř oboru názvů (včetně globálního oboru názvů).|
|Úprava|Vytvoří deklaraci [automaticky implementované vlastnosti](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) .|Uvnitř třídy nebo struktury.|
|propfull|Vytvoří deklaraci vlastnosti pomocí přístupových objektů Get a set.|Uvnitř třídy nebo struktury.|
|propg|Vytvoří [automaticky implementovanou vlastnost](https://msdn.microsoft.com/library/aa55fa97-ccec-431f-b5e9-5ac789fd32b7) , která je určená jen pro čtení s privátním přístupovým objektem set.|Uvnitř třídy nebo struktury.|
|Instalační|Vytvoří [statickou](https://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)deklaraci hlavní metody[int](https://msdn.microsoft.com/library/212447b4-5d2a-41aa-88ab-84fe710bdb52) .|Uvnitř třídy nebo struktury.|
|struct|Vytvoří deklaraci [struktury](https://msdn.microsoft.com/library/ff3dd9b7-dc93-4720-8855-ef5558f65c7c) .|V oboru názvů (včetně globálního oboru názvů), třídy nebo struktury.|
|svm|Vytvoří [statickou](https://msdn.microsoft.com/library/5509e215-2183-4da3-bab4-6b7e607a4fdf)deklaraci hlavní metody[void](https://msdn.microsoft.com/library/0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4) .|Uvnitř třídy nebo struktury.|
|switch|Vytvoří blok [přepínače](https://msdn.microsoft.com/library/44bae8b8-8841-4d85-826b-8a94277daecb) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|vyzkoušení|Vytvoří blok [try-catch](https://msdn.microsoft.com/library/cb5503c7-bfa1-4610-8fc2-ddcd2e84c438) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|tryf|Vytvoří blok [try-finally](https://msdn.microsoft.com/library/c27623fb-7261-4464-862c-7a369d3c8f0a) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|unchecked|Vytvoří [nekontrolované](https://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) bloky.|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|unsafe|Vytvoří [nebezpečný](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) blok.|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|
|using|Vytvoří direktivu [using](https://msdn.microsoft.com/library/b42b8e61-5e7e-439c-bb71-370094b44ae8) .|Uvnitř oboru názvů (včetně globálního oboru názvů).|
|while|Vytvoří smyčku [while](https://msdn.microsoft.com/library/72a0765c-6852-4aca-b327-4a11cb7f5c59) .|Uvnitř metody, indexeru, přistupujícího objektu vlastnosti nebo přístupového objektu události.|

## <a name="see-also"></a>Viz také
 Fragmenty kódu [funkce fragment kódu](../ide/code-snippet-functions.md) [Code Snippets](../ide/code-snippets.md) [: vytvoření nového fragmentu s](https://msdn.microsoft.com/8d56d43c-097a-475b-aa85-cae1554b6338) [parametry šablony](../ide/template-parameters.md) nahrazení [Postupy: použití funkce obklopit s fragmenty kódu](../ide/how-to-use-surround-with-code-snippets.md) [Postupy: obnovení fragmentů refaktoringu jazyka C#](../ide/how-to-restore-csharp-refactoring-snippets.md)
