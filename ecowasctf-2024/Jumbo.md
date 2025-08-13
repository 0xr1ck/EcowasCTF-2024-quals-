brief `A developer from the marketing department is working on an e-commerce application built with Laravel. Your task as an AppSec specialist is to analyze the running application in the staging environment and spot vulnerabilities and their impact.

#### Prerequisites

- The staging web server is running on port 80 
- You're provided the source code zipped in the artifacts section 
- Multiple choice questions are all-or-nothing 
- Answers are case-insensitive` 

### Source Code 
first question is 

```
Q1

Which of the following methods in the OrderController is vulnerable to SQL Injection?

![trophy](https://cyberlab.sec-dojo.com/assets/icons/trophy.svg)

5 points

1 Attempt remaining

- A. index()
- B. orderDetails($id)
- C. reviewOrder(Request $request)
- D. submitReview(Request $request)

```

oderconller.php 

```php 
<?php

  

namespace App\Http\Controllers;
use App\Models\Order as ModelsOrder;
use App\Models\Product as ModelsProduct;
use App\Models\OrderDetail as ModelsOrderDetail;
use App\Models\Review as ModelsReview;
use Illuminate\Http\Request;

  
class OrderController extends Controller
{
public static function index()

{
$pageName = 'Orders List';
$orders = ModelsOrder::where('user_id', auth()->user()->id)->with('orderDetails')->orderBy('created_at', 'desc')->paginate(10);
$data = compact('orders', 'pageName');
return view('orders')->with($data);

}
public static function orderDetails($id)
{

$orders = ModelsOrder::whereRaw("id = '$id'")->with('orderDetails')->first();
$pageName = "Order Details $id";
$productDetails = [];
foreach ($orders->toArray()['order_details'] as $order) {
$product = ModelsProduct::where('bmuk_no', $order['bmuk_no'])->first()->toArray();
$productDetails[$order['bmuk_no']] = $product;

}
$data = compact('orders', 'productDetails', 'pageName');
return view('orderdetails')->with($data);
}

public static function reviewOrder(Request $request)

{
$pageName = 'Review Order';
$order = ModelsOrderDetail::whereRaw("order_id = '{$request->order_id}' AND bmuk_no = '{$request->bmuk_no}'")->first();
$product = ModelsProduct::where('bmuk_no', $order['bmuk_no'])->first()->toArray();
$orderid = $request->order_id;
$data = compact('product', 'orderid', 'pageName');
return view('revieworder')->with($data);

}
  
public static function submitReview(Request $request)
{
ModelsReview::create([
'user_id' => auth()->user()->id,
'product_id' => $request->product_id,
'order_id' => $request->order_id,
'rating' => $request->score,
'comment' => $request->comment,
]);
return redirect()->route('orderdetails', ['orderNo' => $request->order_id])->with('toastSuccess', 'Review submitted successfully');
}

}
```

the answer is B ` orderDetails($id) - $orders = ModelsOrder::whereRaw("id = '$id'")->with('orderDetails')->first(); `  here the $id is directly in to the sql query string without sanitization.

```d
Q2 What type of SQL Injection vulnerability is likely present in the vulnerable method(s) in OrderController?

- A. Second-order SQL Injection
- B. Parameterized Queries Injection
- C. Error-based SQL Injection
- D. Blind SQL Injection
```


