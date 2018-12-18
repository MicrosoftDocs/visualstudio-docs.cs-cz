---
title: Přírůstková sestavení | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, incremental builds
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8e877d6383a4a4257fa72fde0d1daf4a91626025
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39079213"
---
# <a name="incremental-builds"></a>Přírůstková sestavení
Přírůstková sestavení jsou sestavení, která jsou optimalizována tak, aby cíle, které mají výstupní soubory, jež jsou aktuální s ohledem na jejich odpovídající vstupní soubory, již nebyly prováděny. Cílový prvek může mít atribut `Inputs`, který určuje, jaké vstupní položky jsou z hlediska cíle očekávány, a atribut `Outputs`, který určuje položky vytvořené na výstupu. Nástroj MSBuild se mezi hodnotami těchto atributů pokouší nalézt mapování 1 : 1. Pokud mapování 1 : 1 existuje, porovná nástroj MSBuild časové razítko každé vstupní položky s časovým razítkem odpovídající položky na výstupu. Výstupní soubory, které nemají mapování 1 : 1, jsou porovnány se všemi vstupními soubory. Položka je považována za aktuální, pokud je její výstupní soubor stejně starý nebo novější než její vstupní soubor(y).  
  
 Jsou-li všechny výstupní položky aktuální, je cíl nástrojem MSBuild vynechán. To *přírůstkového sestavení* cíle může výrazně zlepšit rychlost sestavení. Jsou-li aktuální jen některé soubory, nástroj MSBuild spustí cíl, ale vynechá aktuální položky a tím změní všechny položky na aktuální. Tento proces se označuje jako *částečné přírůstkové sestavení*.  
  
 Mapování 1 : 1 jsou obvykle tvořena transformací položek. Další informace najdete v tématu [transformuje](../msbuild/msbuild-transforms.md).  
  
 Uvažujme následující cíl.  
  
```xml  
<Target Name="Backup" Inputs="@(Compile)"   
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">  
    <Copy SourceFiles="@(Compile)" DestinationFiles=  
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />  
</Target>  
```  
  
 Sada souborů, které jsou reprezentována `Compile` typ položky je zkopírován do záložního adresáře. Záložní soubory mají *.bak* příponu názvu souboru. Pokud nejsou soubory, které jsou určeny typem položky `Compile`, nebo odpovídající záložní soubory odstraněny nebo změněny po spuštění cíle zálohování, dojde v následujících sestaveních k vynechání cíle zálohování.  
  
## <a name="output-inference"></a>Odvození výstupu  
 Nástroj MSBuild porovnává cílové atributy `Inputs` a `Outputs`, aby určil, zda bude cíl proveden. V ideálním případě nedojde po dokončení přírůstkového sestavení ke změně existující sady souborů bez ohledu na spuštění přidružených cílů. Vzhledem k tomu, že vlastnosti a položky vytvořené nebo upravené pomocí úkolů mohou ovlivnit sestavení, musí nástroj MSBuild odvodit jejich hodnoty i v případě vynechání cíle, který je ovlivňuje. Tento proces se označuje jako *odvození výstupu*.  
  
 Existují tři případy:  
  
-   Cíl obsahuje atribut `Condition`, který je vyhodnocen jako `false`. Cíl v tomto případě není spuštěn a nemá žádný vliv na sestavení.  
  
-   Cíl obsahuje neaktuální výstupy a je spuštěn je aktuální.  
  
-   Cíl neobsahuje žádné neaktuální výstupy a je přeskočen. Nástroj MSBuild vyhodnotí cíl a provede změny u položek a vlastností, jako kdyby byl cíl spuštěn.  

Pro podporu přírůstkové kompilace musí úkoly zajistit, aby byla hodnota atributu `TaskParameter` jakéhokoli prvku `Output` rovna vstupnímu parametru úkolu. Následuje několik příkladů:  
  
```xml  
<CreateProperty Value="123">  
    <Output PropertyName="Easy" TaskParameter="Value" />  
</CreateProperty>  
```  
  
 Tento kód vytvoří vlastnost Easy, která má hodnotu "123", zda je cíl proveden nebo vynechán.  
  
```xml  
<CreateItem Include="a.cs;b.cs">  
    <Output ItemName="Simple" TaskParameter="Include" />  
</CreateItem>  
```  
  
 Tento kód vytvoří typ položky Simple, která má dvě položky, *a.cs* a *b.cs*, zda je cíl proveden nebo vynechán.  
  
 Při spuštění nástroje MSBuild 3.5 se u skupin položek a vlastností v cíli automaticky provede odvození výstupu. Úkoly `CreateItem` nejsou v cíli vyžadovány a je třeba se jim vyhnout. Úkoly `CreateProperty` by měly být použity v cíli pouze k určení toho, zda byl cíl spuštěn.  
  
## <a name="determine-whether-a-target-has-been-run"></a>Určení, zda byl cíl spuštěn  
 Vzhledem k odvození výstupu je pro prozkoumání vlastností a položek nutné do cíle přidat úkol `CreateProperty`, aby bylo možné určit, zda byl cíl proveden. Přidejte úkol `CreateProperty` do cíle a přiřaďte mu prvek `Output`, jehož `TaskParameter` je „ValueSetByTask“.  
  
```xml  
<CreateProperty Value="true">  
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />  
</CreateProperty>  
```  
  
 Tento kód vytvoří vlastnost CompileRan a dá jí hodnotu `true`, ale pouze v případě, že je cíl proveden. Pokud je cíl vynechán, nebude vlastnost CompileRan vytvořena.  
  
## <a name="see-also"></a>Viz také:  
 [Cíle](../msbuild/msbuild-targets.md)