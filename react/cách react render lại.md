Ta biết react sử dụng dom ảo, nghĩa là, lần đầu tiên chương trình render, nó render thành dom ảo r bê nguyên thành dom thật luôn, từ các lần render lại sau, nó sẽ so sánh cái dom ảo vừa render ra với dom ảo cũ ( cx chính là dom thật hiện tại ) xem có chỗ nào khác nhau r render sự khác nhau đó lên dom thật, chứ ko render lại toàn bộ dom thật.

Để render lại, fai có cái kích hoạt nó, ở đây ta biết hàm setstate() hay hàm forceupdate(), ở đây ta châc chắn khi render lại nó sẽ render chính component kích hoạt sự render và toàn bộ component con của nó, dù cho cái state của component này có liên quan đến các component con hay k. Khi render toàn bộ xong, nó so sánh dom ảo cũ r render ra dom thật.

Vấn đề là khi render lại, nó ko chạy toàn bộ code ( ví dụ như hàm khởi tạo chả bao h chạy lại ) nên kể cả trong đấy nó đã có sự thay đổi thì nó cx chả load lại, nó chỉ load lại các cái trong hàm render() ( và 1 số hàm đặc biệt khác ), tóm lại nếu 1 biến x = data dc gán bên ngoài hàm render(), nếu data thay đổi thì khi render lại x ko thay đổi

Đối với function component, nó load lại toàn bộ function, trừ trường hợp trong func đó có code ví dụ như:

const [stateChild,setStateChild] = useState(props.value);

thì props thay đổi, code trên ko dc chạy lại ( có vẻ nó dc coi như 1 hàm khởi tạo )

Đối với func component dùng redux, hàm setSelector() lại dc chạy lại khi state thay đổi.