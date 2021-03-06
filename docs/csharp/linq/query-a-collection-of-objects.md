---
title: 查询对象集合（C# 中的 LINQ）
description: 了解如何使用 C# 中的 LINQ 查询集合。
ms.date: 11/30/2016
ms.assetid: 87a76f8a-0b58-4791-90ea-2fe0a30416c9
ms.openlocfilehash: 7bc59e7009f9ae8d8f66c24e9519d9100404c9c4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511379"
---
# <a name="query-a-collection-of-objects"></a>查询对象的集合

此示例演示如何对一系列 `Student` 对象执行简单查询。 每个 `Student` 对象均包含一些关于学生的基本信息和表示学生在四门考试中的分数的列表。  
  
该应用程序充当本部分中使用相同 `students` 数据源的许多其他示例的框架。  
  
## <a name="example"></a>示例

以下查询将返回在第一堂考试中得分为 90 或更高的学生。  
  
[!code-csharp[csProgGuideLINQ#15](~/samples/snippets/csharp/concepts/linq/how-to-query-a-collection-of-objects_1.cs)]  
  
该查询有意简单，以使你可以进行实验。 例如，你可以在 `where` 子句中尝试其他条件或使用 `orderby` 子句对结果进行排序。  
  
## <a name="see-also"></a>请参阅

- [语言集成查询 (LINQ)](index.md)  
- [字符串内插](../language-reference/tokens/interpolated.md)