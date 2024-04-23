# HƯỚNG DẪN SỬ DỤNG STABLE DIFFUSION ĐỂ TẠO RA NHỮNG HÌNH ẢNH CHẤT LƯỢNG

## Chọn model stable diffusion nào?

Hiện tại, stable diffusion được phát triển thành các bản 1.5, 2.0, 2.1 và XL và 1 cộng đồng phát triển model này với nhiều phiên bản khác nhau nhằm tạo ra những model tạo sinh hình ảnh có chất lượng tốt. Có thể liệt kê 1 vài model chất lượng được cộng đồng đánh giá và sử dụng nhiều:
- Stable Diffusion 1.5
- Stable Diffusion 2.1
- Stable Diffusion XL base
- DreamShaperXL
- XL lighting

## txt2img, img2img và inpaint

### txt2img
!['txt to image'](image.png)

- Là tính năng chính của model, cách sử dụng khá đơn giản, bạn chỉ cần nhập 1 số từ ngữ/nội dung (bằng tiếng anh nhé) mà bạn muốn tạo ra ví dụ:
```
a beautiful woman dance, coffee shop, cinematic light, realistic, photography
```
để có thể chọn được 1 hình ảnh có nội dung và bối cảnh như mong muốn, bạn có thể dụng 1 số thông số sau để cải thiện quá trình tạo sinh

`Sampling method`: có nhiều method, bạn có thể dùng `DPM++ 2M`, `DDIM`, `Euler a`

`Schedule type`: nên sử dụng `Uniform`

`Sample steps`: steps các cao thì ảnh gen ra sẽ có nhiều chi tiết hơn nhưng sẽ lâu hơn

`Width` và `Height`: kích thước của ảnh gen ra

`CFG Scale`: (Classifier Free Guidance scale) thông số này để model sinh ảnh phải/tự do theo câu lệnh của bạn, thông số thấp sẽ model sẽ tự do sáng tạo, thông số càng cao model sẽ gen gần xác với yêu cầu. CFG 2-7 là thấp, 7-10 là cân bằng, 10-15 theo sát câu lệnh, 15> cần câu lệnh chi tiết để mô tả cụ thể từng chi tiết 

![alt text](image-1.png)

### img2img
![alt text](image-7.png)
Khi đã chọn được 1 hình ảnh hợp với nội dung (bỏ qua chi tiết, sẽ có 1 số model gen ra hình xấu, ko logic, ...). Bây giờ bạn có thể dùng img2img để gen lại hình ảnh đó để có tính logic và yêu cầu hợp lý hơn. Hãy chú ý thông số sau:

`Schedule type`: bây giờ bạn nên chọn `karras`

`Denoising strength`: để gen ra các bố cảnh tương tự những các chi tiết khác sẽ thay đổi thì bạn nên chọn từ 0.6 - 0.8, nếu bạn muốn giữ lại các bối cảnh thì chọn 0.3-0.6

### inpaint
![alt text](image-8.png)
Với công cụ này, bạn có thể thay đổi nội dung, chi tiết cụ thể ở 1 vùng nhất định, để sử dụng hiệu quả bạn cần lưu ý các thông số sau:

`Inpaint area`: chọn `Only masked`

`resize to`: nên chọn resolution thấp hơn ảnh bạn sẽ gen ra, 1 ví dụ để bạn dễ hình dung

`Denosising strength`: thông số này tương tự ở `img2img`, nếu bạn muốn vùng thay đổi chỉ gen ra hình theo câu lệnh mới bạn đặt ra thì có thể chọn 0.4 - 0.5

![alt text](image-9.png)

### super resolution:

kích thước hình ảnh gen ra tối đa là 768x768 nên khi gen ra được 1 hình ảnh đẹp các bạn cần 1 công cụ để tăng kích thước của hình ảnh đó. Sự dụng `Extras` và thao tác sau để tăng kích thước hình ảnh:

`Upscale 1`: chọn `R-ESRGAN 4x+`

`Resize`: chọn số lần muốn up lên (tối đa là x8)

### ControlNet

Tính năng `ControlNet` sẽ giúp bạn tạo ra những hình ảnh theo 1 chuẩn được đặt ra làm cho việc tạo sinh hình ảnh trở nên dễ kiểm soát hơn

### mode canny
![alt text](image-2.png)
- Để sử dụng được mode canny bạn cần 1 hình ảnh có sẵn và chú ý thêm 1 số thông số sau:
`Canny Low Threshold` và `Canny High Threshold`: điều chỉnh 2 thông số này để tìm điểm màu trong ngưỡng đã set 

- Tiếp sau đó bạn có thể add thêm 1 số câu lệnh để tăng độ chính xác cho hình ảnh, model nên chọn ở đây là `DreamShaperXL`
![alt text](image-3.png)
### mode openpose
![alt text](image-4.png)
- Đối với `openPose` bạn có thể chọn ![alt text](image-6.png) tại thông số `Proprocessor`, khuyên dùng `openpose_full` nếu có cả tay, thân và mặt

- Cũng như mode trên, bạn có thể add thêm 1 số câu lệnh để tăng độ chính xác cho hình ảnh, model nên chọn là `DreamShaperXL`

![alt text](image-5.png)

### References:
[ControlNet github](https://github.com/lllyasviel/ControlNet)

[ControlNet extension](https://github.com/Mikubill/sd-webui-controlnet)
### DreamBooth train your style

### Plugin Photoshop:

[Plugin PTS](https://github.com/isekaidev/stable.art)

[Auto-Photoshop-StableDiffusion-Plugin](https://github.com/AbdullahAlfaraj/Auto-Photoshop-StableDiffusion-Plugin?tab=readme-ov-file)

[Show case](https://www.youtube.com/watch?v=VL_gbQai79E)